<svelte:options tag="zoo-tooltip"></svelte:options>
<div class="holder" bind:this={_tooltipRoot}>
	<div class="box {position} {hidden ? 'hide' : 'show'}">
		<div class="tooltip-content">
			<slot>
				{#if text}<span class="text">{text}</span>{/if}
			</slot>
		</div>
		<div class="tip"></div>	
	</div>
</div> 

<style type='text/scss'>
	@import "variables";
	:host {
		display: flex;
		position: absolute;
		width: 100%;
		height: 100%;
		z-index: 9999;
		left: 0;
		bottom: 0;
		pointer-events: none;
		line-height: initial;
		font-size: initial;
		font-weight: initial;
		contain: layout;
		justify-content: center;
		color: black;
	}
	.holder {
		width: 100%;
	}
	.box {
		transition: opacity 0.3s, transform 0.3s;
		pointer-events: initial;
		box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.12), 0 2px 12px 0 rgba(0, 0, 0, 0.12);
		border-radius: 3px;
		position: absolute;
		&.top {
			bottom: calc(100% + 14px);
			.tip {
				width: 0;
				right: calc(50% + 8px);
			}
		}
		&.right {
			left: 98%;
			top: 50%;
			.tip {
				bottom: 50%;
				left: -8px;
				right: 100%;
			}
		}
		&.bottom {
			top: 98%;
			right: 50%;
			.tip {
				top: 0;
				width: 0px;
				right: calc(50% + 8px);
			}
		}
		&.left {
			left: 2%;
			top: 50%;
			.tip {
				bottom: 50%;
				right: 8px;
				width: 0px;
			}
		}
	}
	.box.hide {
		opacity: 0;
		&.top {transform: translate3d(0,10%,0);}
		&.right {transform: translate3d(18%,-50%,0);}
		&.bottom {transform: translate3d(50%,30%,0);}
		&.left {transform: translate3d(-120%,-50%,0);}
	}
	.box.show {
		opacity: 1;
		&.top {transform: translate3d(0,0,0);}
		&.right {transform: translate3d(8%,-50%,0);}
		&.bottom {transform: translate3d(50%,20%,0);}
		&.left {transform: translate3d(-110%,-50%,0);}
	}
	.tooltip-content {
	  padding: 10px;
	  font-size: 15px;
	  position: relative;
	  z-index: 1;
	  background: white;
	  border-radius: 3px;
	  display: inline-block;
	  min-width: 150px;
		text-align: center;
	  .text {
		  white-space: pre;
	  }
	}
	.tip {
		position: absolute;
		right: 50%;
		width: 16px;
		&:after {
			content: "";
			width: 16px;
			height: 16px;
			position: absolute;
			box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.12), 0 2px 12px 0 rgba(0, 0, 0, 0.12);
			top: -8px;
			transform: rotate(45deg);
			z-index: 0;
    		background: white;
		}
	}
	::slotted(*) {
		pointer-events: all;
	}
</style>

<script>
	import { afterUpdate } from 'svelte';

	export let text = '';
	export let position = 'top'; // left, right, bottom
	export let target = '';
	export let targetprop;
	export let behaviour = 'hover'; //click

	let hidden = true;
	let tooltipTarget;
	let _tooltipRoot;
	let prevBeh;
	let timeout;

	afterUpdate(() => {
		if (!tooltipTarget && target){
			tooltipTarget = document.querySelector('#' + target);
			attachListeners();
		} else if (!tooltipTarget && targetprop){
			tooltipTarget = targetprop;
			attachListeners();
		}
		if (behaviour !== prevBeh) {
			prevBeh = behaviour;
			attachListeners();
		}
	});

	const attachListeners = () => {
		if (!tooltipTarget) return;
		_tooltipRoot.addEventListener('mouseenter', e => {
			clearTimeout(timeout);
			hidden = false;
		});
		switch (behaviour) {
			case 'hover':
				tooltipTarget.removeEventListener('click', e => hidden ? show() : hide(), false);
				tooltipTarget.addEventListener('mouseenter', show);
				tooltipTarget.addEventListener('mouseleave', mouseleave);
				break;
			case 'click':
				tooltipTarget.removeEventListener('mouseenter', show, false);
				tooltipTarget.removeEventListener('mouseleave', mouseleave, false);
				tooltipTarget.addEventListener('click', e => hidden ? show() : hide());
				break;
			default:
				break;
		}
	}

	const mouseleave = e => {
		if (e.relatedTarget !== _tooltipRoot.getRootNode().host) {
			hide();
		}
	}

	const show = () => {
		_tooltipRoot.style.display = 'flex';
		setTimeout(() => {
			hidden = false;
		}, 40);
	}
	const hide = () => {
		hidden = true;
		timeout = setTimeout(() => {
			_tooltipRoot.style.display = 'none';
		}, 300);
	}
</script>