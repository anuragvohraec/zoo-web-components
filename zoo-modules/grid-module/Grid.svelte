<svelte:options tag="zoo-grid"></svelte:options>
<table>
    <thead>
        <slot bind:this="{header}" name="header"></slot>
    </thead>
    <tbody>
        <slot bind:this="{row}" name="row"></slot>
    </tbody>
    <tfoot>
        <slot bind:this="{footer}" name="footer"></slot>
    </tfoot>
</table>

<style type="text/scss">
	@import "variables";

	:host {
		display: block;
	}

	table {
		border-collapse: collapse;
		border-spacing: 0px;
		width: 100%;
		height: 100%;
	}

	::slotted(tr:nth-child(2n)) {
		background: $anti-flash-white;
	}

	::slotted(tr[disabled]) {
		background: $grey-chateau;
		cursor: not-allowed;
	}

	::slotted(tr[header]) {
		color: $grey;
		font-weight: bold;
		background: white;
	}

	::slotted(tr[footer]) {
		color: $grey;
		font-weight: bold;
		background: white;
	}

	::slotted(tr) {
		text-align: left;
	}

	::slotted(tr[row]:hover) {
		background: $whisper;
	}

	::slotted(tr[disabled]:hover) {
		background: $grey-chateau;
	}
</style>

<script>
    import { onMount } from 'svelte';
    let header;
    let footer;
    let row;

    onMount(() => {
        attachFunctionAttributes(header, 'header');
        attachFunctionAttributes(footer, 'footer');
        attachFunctionAttributes(row, 'row');
    });

    const attachFunctionAttributes = (el, name) => {
        el.addEventListener('slotchange', () => {
            const nodes = el.assignedNodes();
            for (const node of nodes) {
                node.setAttribute(name, '');
                for (const childNode of node.childNodes) {
                    if(childNode.nodeName == "TD" || childNode.nodeName == "TH") {
                        childNode.style.padding = '10px 5px';
                    }
                }
            }
        });
    }
</script>