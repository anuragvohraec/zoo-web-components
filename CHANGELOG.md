# 4.0.9
`zoo-seachable-select` improved keyboard user experience while using this element.

# 4.0.8
`zoo-seachable-select` improved keyboard user experience while using this element.
`zoo-input` - type `date` and `time` now doesn't fall back to native inputs but is more styled like other inputs.

# 4.0.7
`zoo-seachable-select` now performs full text scan instead of checking whether something starts with input value.

# 4.0.6
Fixed label alignment for `InputLabel`.

# 4.0.5
Fixed iife prod build not to export classes.

# 4.0.1
`zoo-footer` now accepts `copyright` attribute to show name of the company for example.

# 4.0.0
Included possibility for theming and new component `zoo-collapsable-list`.

# 3.0.1
Added iife export back again. how both `iife` and `esm` versions will be published and the user will decide which one to use.

# 3.0.0
Rename all components from `zoo-log-...` to `zoo-...`.
Project internals cleanup.
Changed export from `iife` to `esm`.

# 2.5.2
`zoo-log-searchable-select` aligned behaviour of multiple and single select elements.

# 2.5.1
`zoo-log-searchable-select` fixed not setting input value on selecting options.

# 2.5.0
Added some interactivity to Button, Link, Modal and Tooltip elements.

# 2.4.4
Various UX improvements.

# 2.4.2
`zoo-log-select` Using single svg for select arrows instead of 2.

# 2.4.2
`zoo-log-radio` extended to handle focus and blur events.

# 2.4.1
`zoo-log-radio` fix error state change when not using `template`.

# 2.4.0
Created `zoo-log-radio`.

# 2.3.5
Extended `zoo-log-checkbox` to handle enter keypress and react to focus event.

# 2.3.4
Wrapped SVGs to preserve static width and height to avoid change of size depending on the size of sibling node text.

# 2.3.3
Optimized size of svg, causing the library to lose 10 Kbytes minified and about 2.5KB gzipped.

# 2.3.2
`zoo-log-select` - reduced the size of arrows and made them more aligned.

# 2.3.1
`zoo-log-searchable-select` placeholder now shows initial placeholder when no options are selected and selected options separated with `,` otherwise.

# 2.3.0
REMOVED `folding` option from `zoo-log-tooltip`.
`zoo-log-searchable-select` now shows tooltip on hover on itself or on the tooltip.

# 2.2.0
`zoo-log-tooltip` now accepts another option `folding`. When `folding` is true, tooltip will have length of 60px and overflow hidden. The content will show up on hover;
Additional minor css fixes for `zoo-log-searchable-select`.

# 2.0.5
`zoo-log-searchable-select` now has a fallback to standard `zoo-log-select` when user is on mobile browser.
Covered all components with tests.
Minor clean-ups here and there.

# 2.0.1
Added `zoo-log-searchable-select` to component lists.

# 2.0.0
BREAKING CHANGE: `zoo-log-header`, `zoo-log-modal` and `zoo-log-navigation` now doesn't accept named slots. Just define slotted content as regular HTMLElement, for example:      
## Before:
```
<zoo-log-navigation class="nav">
	<div slot="content">
		{#each navlinks as link}
			<zoo-log-link href="{link.href}" target="{link.target}" type="{link.type}"
				text="{link.text}">
			</zoo-log-link>
		{/each}
	</div>
</zoo-log-navigation>
```
## After
```
<zoo-log-navigation class="nav">
	<div>
		{#each navlinks as link}
			<zoo-log-link href="{link.href}" target="{link.target}" type="{link.type}"
				text="{link.text}">
			</zoo-log-link>
		{/each}
	</div>
</zoo-log-navigation>
```

# 1.2.0
BREAKING CHANGE: refer to README.md for Button element as the slots for that element has changed. Now the `<button>` element is embedded inside web-component, while the content of the button can still be injected from external source.