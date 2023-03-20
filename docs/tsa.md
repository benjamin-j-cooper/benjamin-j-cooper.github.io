---
layout: default
title: Time Series Analysis
description: This is an analysis of Covid 19 data from Johns Hopkins 
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Covid19_analysis</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .pm { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation.Marker */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>



<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
  scrollbar-width: thin;
}

/*
 * Webkit scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-corner {
  background: var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-thumb {
  background: rgb(var(--jp-scrollbar-thumb-color));
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-right: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-bottom: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar */

[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-corner,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-corner {
  background-color: transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-thumb,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid transparent;
  border-right: var(--jp-scrollbar-endpad) solid transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid transparent;
  border-bottom: var(--jp-scrollbar-endpad) solid transparent;
}

/* tiny scrollbar */

.jp-scrollbar-tiny::-webkit-scrollbar,
.jp-scrollbar-tiny::-webkit-scrollbar-corner {
  background-color: transparent;
  height: 4px;
  width: 4px;
}

.jp-scrollbar-tiny::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
  border-left: 0px solid transparent;
  border-right: 0px solid transparent;
}

.jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
  border-top: 0px solid transparent;
  border-bottom: 0px solid transparent;
}

/*
 * Phosphor
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Widget, /* </DEPRECATED> */
.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  cursor: default;
}


/* <DEPRECATED> */ .p-Widget.p-mod-hidden, /* </DEPRECATED> */
.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-CommandPalette, /* </DEPRECATED> */
.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-CommandPalette-search, /* </DEPRECATED> */
.lm-CommandPalette-search {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-content, /* </DEPRECATED> */
.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-CommandPalette-header, /* </DEPRECATED> */
.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}


/* <DEPRECATED> */ .p-CommandPalette-item, /* </DEPRECATED> */
.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}


/* <DEPRECATED> */ .p-CommandPalette-itemIcon, /* </DEPRECATED> */
.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemContent, /* </DEPRECATED> */
.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}


/* <DEPRECATED> */ .p-CommandPalette-itemShortcut, /* </DEPRECATED> */
.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemLabel, /* </DEPRECATED> */
.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.lm-close-icon {
	border:1px solid transparent;
  background-color: transparent;
  position: absolute;
	z-index:1;
	right:3%;
	top: 0;
	bottom: 0;
	margin: auto;
	padding: 7px 0;
	display: none;
	vertical-align: middle;
  outline: 0;
  cursor: pointer;
}
.lm-close-icon:after {
	content: "X";
	display: block;
	width: 15px;
	height: 15px;
	text-align: center;
	color:#000;
	font-weight: normal;
	font-size: 12px;
	cursor: pointer;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-DockPanel, /* </DEPRECATED> */
.lm-DockPanel {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-widget, /* </DEPRECATED> */
.lm-DockPanel-widget {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-tabBar, /* </DEPRECATED> */
.lm-DockPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-DockPanel-handle, /* </DEPRECATED> */
.lm-DockPanel-handle {
  z-index: 2;
}


/* <DEPRECATED> */ .p-DockPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-DockPanel-handle:after, /* </DEPRECATED> */
.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}


/* <DEPRECATED> */ .p-DockPanel-overlay, /* </DEPRECATED> */
.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}


/* <DEPRECATED> */ .p-DockPanel-overlay.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Menu, /* </DEPRECATED> */
.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-Menu-content, /* </DEPRECATED> */
.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-Menu-item, /* </DEPRECATED> */
.lm-Menu-item {
  display: table-row;
}


/* <DEPRECATED> */
.p-Menu-item.p-mod-hidden,
.p-Menu-item.p-mod-collapsed,
/* </DEPRECATED> */
.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}


/* <DEPRECATED> */
.p-Menu-itemIcon,
.p-Menu-itemSubmenuIcon,
/* </DEPRECATED> */
.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}


/* <DEPRECATED> */ .p-Menu-itemLabel, /* </DEPRECATED> */
.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}


/* <DEPRECATED> */ .p-Menu-itemShortcut, /* </DEPRECATED> */
.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-MenuBar, /* </DEPRECATED> */
.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-MenuBar-content, /* </DEPRECATED> */
.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}


/* <DEPRECATED> */ .p--MenuBar-item, /* </DEPRECATED> */
.lm-MenuBar-item {
  box-sizing: border-box;
}


/* <DEPRECATED> */
.p-MenuBar-itemIcon,
.p-MenuBar-itemLabel,
/* </DEPRECATED> */
.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-ScrollBar, /* </DEPRECATED> */
.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-ScrollBar-button, /* </DEPRECATED> */
.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-track, /* </DEPRECATED> */
.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-thumb, /* </DEPRECATED> */
.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-SplitPanel-child, /* </DEPRECATED> */
.lm-SplitPanel-child {
  z-index: 0;
}


/* <DEPRECATED> */ .p-SplitPanel-handle, /* </DEPRECATED> */
.lm-SplitPanel-handle {
  z-index: 1;
}


/* <DEPRECATED> */ .p-SplitPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-SplitPanel-handle:after, /* </DEPRECATED> */
.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabBar, /* </DEPRECATED> */
.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='horizontal'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='vertical'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
  align-items: flex-end;
}


/* <DEPRECATED> */ .p-TabBar-content, /* </DEPRECATED> */
.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='horizontal'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='vertical'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
}


/* <DEPRECATED> */
.p-TabBar-tabIcon,
.p-TabBar-tabCloseIcon,
/* </DEPRECATED> */
.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-TabBar-tabLabel, /* </DEPRECATED> */
.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}


.lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
}


/* <DEPRECATED> */ .p-TabBar-tab.p-mod-hidden, /* </DEPRECATED> */
.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}


.lm-TabBar-addButton.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-TabBar.p-mod-dragging .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

.lm-TabBar-tabLabel .lm-TabBar-tabInput {
  user-select: all;
  width: 100%;
  box-sizing : border-box;
  background: inherit;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabPanel-tabBar, /* </DEPRECATED> */
.lm-TabPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-TabPanel-stackedPanel, /* </DEPRECATED> */
.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

@charset "UTF-8";
html{
  -webkit-box-sizing:border-box;
          box-sizing:border-box; }

*,
*::before,
*::after{
  -webkit-box-sizing:inherit;
          box-sizing:inherit; }

body{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none;
  color:#182026;
  font-family:-apple-system, "BlinkMacSystemFont", "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Open Sans", "Helvetica Neue", "Icons16", sans-serif; }

p{
  margin-bottom:10px;
  margin-top:0; }

small{
  font-size:12px; }

strong{
  font-weight:600; }

::-moz-selection{
  background:rgba(125, 188, 255, 0.6); }

::selection{
  background:rgba(125, 188, 255, 0.6); }
.bp3-heading{
  color:#182026;
  font-weight:600;
  margin:0 0 10px;
  padding:0; }
  .bp3-dark .bp3-heading{
    color:#f5f8fa; }

h1.bp3-heading, .bp3-running-text h1{
  font-size:36px;
  line-height:40px; }

h2.bp3-heading, .bp3-running-text h2{
  font-size:28px;
  line-height:32px; }

h3.bp3-heading, .bp3-running-text h3{
  font-size:22px;
  line-height:25px; }

h4.bp3-heading, .bp3-running-text h4{
  font-size:18px;
  line-height:21px; }

h5.bp3-heading, .bp3-running-text h5{
  font-size:16px;
  line-height:19px; }

h6.bp3-heading, .bp3-running-text h6{
  font-size:14px;
  line-height:16px; }
.bp3-ui-text{
  font-size:14px;
  font-weight:400;
  letter-spacing:0;
  line-height:1.28581;
  text-transform:none; }

.bp3-monospace-text{
  font-family:monospace;
  text-transform:none; }

.bp3-text-muted{
  color:#5c7080; }
  .bp3-dark .bp3-text-muted{
    color:#a7b6c2; }

.bp3-text-disabled{
  color:rgba(92, 112, 128, 0.6); }
  .bp3-dark .bp3-text-disabled{
    color:rgba(167, 182, 194, 0.6); }

.bp3-text-overflow-ellipsis{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal; }
.bp3-running-text{
  font-size:14px;
  line-height:1.5; }
  .bp3-running-text h1{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h1{
      color:#f5f8fa; }
  .bp3-running-text h2{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h2{
      color:#f5f8fa; }
  .bp3-running-text h3{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h3{
      color:#f5f8fa; }
  .bp3-running-text h4{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h4{
      color:#f5f8fa; }
  .bp3-running-text h5{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h5{
      color:#f5f8fa; }
  .bp3-running-text h6{
    color:#182026;
    font-weight:600;
    margin-bottom:20px;
    margin-top:40px; }
    .bp3-dark .bp3-running-text h6{
      color:#f5f8fa; }
  .bp3-running-text hr{
    border:none;
    border-bottom:1px solid rgba(16, 22, 26, 0.15);
    margin:20px 0; }
    .bp3-dark .bp3-running-text hr{
      border-color:rgba(255, 255, 255, 0.15); }
  .bp3-running-text p{
    margin:0 0 10px;
    padding:0; }

.bp3-text-large{
  font-size:16px; }

.bp3-text-small{
  font-size:12px; }
a{
  color:#106ba3;
  text-decoration:none; }
  a:hover{
    color:#106ba3;
    cursor:pointer;
    text-decoration:underline; }
  a .bp3-icon, a .bp3-icon-standard, a .bp3-icon-large{
    color:inherit; }
  a code,
  .bp3-dark a code{
    color:inherit; }
  .bp3-dark a,
  .bp3-dark a:hover{
    color:#48aff0; }
    .bp3-dark a .bp3-icon, .bp3-dark a .bp3-icon-standard, .bp3-dark a .bp3-icon-large,
    .bp3-dark a:hover .bp3-icon,
    .bp3-dark a:hover .bp3-icon-standard,
    .bp3-dark a:hover .bp3-icon-large{
      color:inherit; }
.bp3-running-text code, .bp3-code{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  font-size:smaller;
  padding:2px 5px; }
  .bp3-dark .bp3-running-text code, .bp3-running-text .bp3-dark code, .bp3-dark .bp3-code{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
  .bp3-running-text a > code, a > .bp3-code{
    color:#137cbd; }
    .bp3-dark .bp3-running-text a > code, .bp3-running-text .bp3-dark a > code, .bp3-dark a > .bp3-code{
      color:inherit; }

.bp3-running-text pre, .bp3-code-block{
  font-family:monospace;
  text-transform:none;
  background:rgba(255, 255, 255, 0.7);
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
  color:#182026;
  display:block;
  font-size:13px;
  line-height:1.4;
  margin:10px 0;
  padding:13px 15px 12px;
  word-break:break-all;
  word-wrap:break-word; }
  .bp3-dark .bp3-running-text pre, .bp3-running-text .bp3-dark pre, .bp3-dark .bp3-code-block{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
  .bp3-running-text pre > code, .bp3-code-block > code{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit;
    font-size:inherit;
    padding:0; }

.bp3-running-text kbd, .bp3-key{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#5c7080;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-family:inherit;
  font-size:12px;
  height:24px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  line-height:24px;
  min-width:24px;
  padding:3px 6px;
  vertical-align:middle; }
  .bp3-running-text kbd .bp3-icon, .bp3-key .bp3-icon, .bp3-running-text kbd .bp3-icon-standard, .bp3-key .bp3-icon-standard, .bp3-running-text kbd .bp3-icon-large, .bp3-key .bp3-icon-large{
    margin-right:5px; }
  .bp3-dark .bp3-running-text kbd, .bp3-running-text .bp3-dark kbd, .bp3-dark .bp3-key{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#a7b6c2; }
.bp3-running-text blockquote, .bp3-blockquote{
  border-left:solid 4px rgba(167, 182, 194, 0.5);
  margin:0 0 10px;
  padding:0 20px; }
  .bp3-dark .bp3-running-text blockquote, .bp3-running-text .bp3-dark blockquote, .bp3-dark .bp3-blockquote{
    border-color:rgba(115, 134, 148, 0.5); }
.bp3-running-text ul,
.bp3-running-text ol, .bp3-list{
  margin:10px 0;
  padding-left:30px; }
  .bp3-running-text ul li:not(:last-child), .bp3-running-text ol li:not(:last-child), .bp3-list li:not(:last-child){
    margin-bottom:5px; }
  .bp3-running-text ul ol, .bp3-running-text ol ol, .bp3-list ol,
  .bp3-running-text ul ul,
  .bp3-running-text ol ul,
  .bp3-list ul{
    margin-top:5px; }

.bp3-list-unstyled{
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-list-unstyled li{
    padding:0; }
.bp3-rtl{
  text-align:right; }

.bp3-dark{
  color:#f5f8fa; }

:focus{
  outline:rgba(19, 124, 189, 0.6) auto 2px;
  outline-offset:2px;
  -moz-outline-radius:6px; }

.bp3-focus-disabled :focus{
  outline:none !important; }
  .bp3-focus-disabled :focus ~ .bp3-control-indicator{
    outline:none !important; }

.bp3-alert{
  max-width:400px;
  padding:20px; }

.bp3-alert-body{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-alert-body .bp3-icon{
    font-size:40px;
    margin-right:20px;
    margin-top:0; }

.bp3-alert-contents{
  word-break:break-word; }

.bp3-alert-footer{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:reverse;
      -ms-flex-direction:row-reverse;
          flex-direction:row-reverse;
  margin-top:10px; }
  .bp3-alert-footer .bp3-button{
    margin-left:10px; }
.bp3-breadcrumbs{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  cursor:default;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:wrap;
      flex-wrap:wrap;
  height:30px;
  list-style:none;
  margin:0;
  padding:0; }
  .bp3-breadcrumbs > li{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }
    .bp3-breadcrumbs > li::after{
      background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M10.71 7.29l-4-4a1.003 1.003 0 00-1.42 1.42L8.59 8 5.3 11.29c-.19.18-.3.43-.3.71a1.003 1.003 0 001.71.71l4-4c.18-.18.29-.43.29-.71 0-.28-.11-.53-.29-.71z' fill='%235C7080'/%3e%3c/svg%3e");
      content:"";
      display:block;
      height:16px;
      margin:0 5px;
      width:16px; }
    .bp3-breadcrumbs > li:last-of-type::after{
      display:none; }

.bp3-breadcrumb,
.bp3-breadcrumb-current,
.bp3-breadcrumbs-collapsed{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  font-size:16px; }

.bp3-breadcrumb,
.bp3-breadcrumbs-collapsed{
  color:#5c7080; }

.bp3-breadcrumb:hover{
  text-decoration:none; }

.bp3-breadcrumb.bp3-disabled{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-breadcrumb .bp3-icon{
  margin-right:5px; }

.bp3-breadcrumb-current{
  color:inherit;
  font-weight:600; }
  .bp3-breadcrumb-current .bp3-input{
    font-size:inherit;
    font-weight:inherit;
    vertical-align:baseline; }

.bp3-breadcrumbs-collapsed{
  background:#ced9e0;
  border:none;
  border-radius:3px;
  cursor:pointer;
  margin-right:2px;
  padding:1px 5px;
  vertical-align:text-bottom; }
  .bp3-breadcrumbs-collapsed::before{
    background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cg fill='%235C7080'%3e%3ccircle cx='2' cy='8.03' r='2'/%3e%3ccircle cx='14' cy='8.03' r='2'/%3e%3ccircle cx='8' cy='8.03' r='2'/%3e%3c/g%3e%3c/svg%3e") center no-repeat;
    content:"";
    display:block;
    height:16px;
    width:16px; }
  .bp3-breadcrumbs-collapsed:hover{
    background:#bfccd6;
    color:#182026;
    text-decoration:none; }

.bp3-dark .bp3-breadcrumb,
.bp3-dark .bp3-breadcrumbs-collapsed{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumbs > li::after{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumb.bp3-disabled{
  color:rgba(167, 182, 194, 0.6); }

.bp3-dark .bp3-breadcrumb-current{
  color:#f5f8fa; }

.bp3-dark .bp3-breadcrumbs-collapsed{
  background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-breadcrumbs-collapsed:hover{
    background:rgba(16, 22, 26, 0.6);
    color:#f5f8fa; }
.bp3-button{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  min-height:30px;
  min-width:30px; }
  .bp3-button > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-button > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-button::before,
  .bp3-button > *{
    margin-right:7px; }
  .bp3-button:empty::before,
  .bp3-button > :last-child{
    margin-right:0; }
  .bp3-button:empty{
    padding:0 !important; }
  .bp3-button:disabled, .bp3-button.bp3-disabled{
    cursor:not-allowed; }
  .bp3-button.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button.bp3-align-right,
  .bp3-align-right .bp3-button{
    text-align:right; }
  .bp3-button.bp3-align-left,
  .bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-button:not([class*="bp3-intent-"]){
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026; }
    .bp3-button:not([class*="bp3-intent-"]):hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-button:not([class*="bp3-intent-"]):active, .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active:hover, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-button.bp3-intent-primary{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover, .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover{
      background-color:#106ba3;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      background-color:#0e5a8a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-primary:disabled, .bp3-button.bp3-intent-primary.bp3-disabled{
      background-color:rgba(19, 124, 189, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-success{
    background-color:#0f9960;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-success:hover, .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-success:hover{
      background-color:#0d8050;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      background-color:#0a6640;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-success:disabled, .bp3-button.bp3-intent-success.bp3-disabled{
      background-color:rgba(15, 153, 96, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-warning{
    background-color:#d9822b;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover, .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover{
      background-color:#bf7326;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      background-color:#a66321;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-warning:disabled, .bp3-button.bp3-intent-warning.bp3-disabled{
      background-color:rgba(217, 130, 43, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-danger{
    background-color:#db3737;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover, .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover{
      background-color:#c23030;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      background-color:#a82a2a;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-button.bp3-intent-danger:disabled, .bp3-button.bp3-intent-danger.bp3-disabled{
      background-color:rgba(219, 55, 55, 0.5);
      background-image:none;
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
    stroke:#ffffff; }
  .bp3-button.bp3-large,
  .bp3-large .bp3-button{
    min-height:40px;
    min-width:40px;
    font-size:16px;
    padding:5px 15px; }
    .bp3-button.bp3-large::before,
    .bp3-button.bp3-large > *,
    .bp3-large .bp3-button::before,
    .bp3-large .bp3-button > *{
      margin-right:10px; }
    .bp3-button.bp3-large:empty::before,
    .bp3-button.bp3-large > :last-child,
    .bp3-large .bp3-button:empty::before,
    .bp3-large .bp3-button > :last-child{
      margin-right:0; }
  .bp3-button.bp3-small,
  .bp3-small .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-button.bp3-loading{
    position:relative; }
    .bp3-button.bp3-loading[class*="bp3-icon-"]::before{
      visibility:hidden; }
    .bp3-button.bp3-loading .bp3-button-spinner{
      margin:0;
      position:absolute; }
    .bp3-button.bp3-loading > :not(.bp3-button-spinner){
      visibility:hidden; }
  .bp3-button[class*="bp3-icon-"]::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    color:#5c7080; }
  .bp3-button .bp3-icon, .bp3-button .bp3-icon-standard, .bp3-button .bp3-icon-large{
    color:#5c7080; }
    .bp3-button .bp3-icon.bp3-align-right, .bp3-button .bp3-icon-standard.bp3-align-right, .bp3-button .bp3-icon-large.bp3-align-right{
      margin-left:7px; }
  .bp3-button .bp3-icon:first-child:last-child,
  .bp3-button .bp3-spinner + .bp3-icon:last-child{
    margin:0 -7px; }
  .bp3-dark .bp3-button:not([class*="bp3-intent-"]){
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover, .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"])[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-large{
      color:#a7b6c2; }
  .bp3-dark .bp3-button[class*="bp3-intent-"]{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:active, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:disabled, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-disabled{
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(255, 255, 255, 0.3); }
    .bp3-dark .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
      stroke:#8a9ba8; }
  .bp3-button:disabled::before,
  .bp3-button:disabled .bp3-icon, .bp3-button:disabled .bp3-icon-standard, .bp3-button:disabled .bp3-icon-large, .bp3-button.bp3-disabled::before,
  .bp3-button.bp3-disabled .bp3-icon, .bp3-button.bp3-disabled .bp3-icon-standard, .bp3-button.bp3-disabled .bp3-icon-large, .bp3-button[class*="bp3-intent-"]::before,
  .bp3-button[class*="bp3-intent-"] .bp3-icon, .bp3-button[class*="bp3-intent-"] .bp3-icon-standard, .bp3-button[class*="bp3-intent-"] .bp3-icon-large{
    color:inherit !important; }
  .bp3-button.bp3-minimal{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button.bp3-minimal:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-minimal:active, .bp3-button.bp3-minimal.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-minimal:disabled, .bp3-button.bp3-minimal:disabled:hover, .bp3-button.bp3-minimal.bp3-disabled, .bp3-button.bp3-minimal.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-minimal{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-minimal:hover, .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-minimal:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-minimal:disabled, .bp3-dark .bp3-button.bp3-minimal:disabled:hover, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover, .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover, .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover, .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover, .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button.bp3-outlined{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    border:1px solid rgba(24, 32, 38, 0.2);
    -webkit-box-sizing:border-box;
            box-sizing:border-box; }
    .bp3-button.bp3-outlined:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button.bp3-outlined:active, .bp3-button.bp3-outlined.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-outlined{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-outlined:hover, .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button.bp3-outlined:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-outlined:active, .bp3-dark .bp3-button.bp3-outlined.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button.bp3-outlined:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover, .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover, .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover, .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover, .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-outlined.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
    .bp3-button.bp3-outlined:disabled, .bp3-button.bp3-outlined.bp3-disabled, .bp3-button.bp3-outlined:disabled:hover, .bp3-button.bp3-outlined.bp3-disabled:hover{
      border-color:rgba(92, 112, 128, 0.1); }
    .bp3-dark .bp3-button.bp3-outlined{
      border-color:rgba(255, 255, 255, 0.4); }
      .bp3-dark .bp3-button.bp3-outlined:disabled, .bp3-dark .bp3-button.bp3-outlined:disabled:hover, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-disabled:hover{
        border-color:rgba(255, 255, 255, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-primary{
      border-color:rgba(16, 107, 163, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
        border-color:rgba(16, 107, 163, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary{
        border-color:rgba(72, 175, 240, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-primary.bp3-disabled{
          border-color:rgba(72, 175, 240, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-success{
      border-color:rgba(13, 128, 80, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
        border-color:rgba(13, 128, 80, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success{
        border-color:rgba(61, 204, 145, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-success.bp3-disabled{
          border-color:rgba(61, 204, 145, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-warning{
      border-color:rgba(191, 115, 38, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
        border-color:rgba(191, 115, 38, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning{
        border-color:rgba(255, 179, 102, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-warning.bp3-disabled{
          border-color:rgba(255, 179, 102, 0.2); }
    .bp3-button.bp3-outlined.bp3-intent-danger{
      border-color:rgba(194, 48, 48, 0.6); }
      .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
        border-color:rgba(194, 48, 48, 0.2); }
      .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger{
        border-color:rgba(255, 115, 115, 0.6); }
        .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-outlined.bp3-intent-danger.bp3-disabled{
          border-color:rgba(255, 115, 115, 0.2); }

a.bp3-button{
  text-align:center;
  text-decoration:none;
  -webkit-transition:none;
  transition:none; }
  a.bp3-button, a.bp3-button:hover, a.bp3-button:active{
    color:#182026; }
  a.bp3-button.bp3-disabled{
    color:rgba(92, 112, 128, 0.6); }

.bp3-button-text{
  -webkit-box-flex:0;
      -ms-flex:0 1 auto;
          flex:0 1 auto; }

.bp3-button.bp3-align-left .bp3-button-text, .bp3-button.bp3-align-right .bp3-button-text,
.bp3-button-group.bp3-align-left .bp3-button-text,
.bp3-button-group.bp3-align-right .bp3-button-text{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto; }
.bp3-button-group{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex; }
  .bp3-button-group .bp3-button{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    position:relative;
    z-index:4; }
    .bp3-button-group .bp3-button:focus{
      z-index:5; }
    .bp3-button-group .bp3-button:hover{
      z-index:6; }
    .bp3-button-group .bp3-button:active, .bp3-button-group .bp3-button.bp3-active{
      z-index:7; }
    .bp3-button-group .bp3-button:disabled, .bp3-button-group .bp3-button.bp3-disabled{
      z-index:3; }
    .bp3-button-group .bp3-button[class*="bp3-intent-"]{
      z-index:9; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:focus{
        z-index:10; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:hover{
        z-index:11; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:active, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-active{
        z-index:12; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:disabled, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-disabled{
        z-index:8; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:first-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:first-child){
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    border-bottom-right-radius:0;
    border-top-right-radius:0;
    margin-right:-1px; }
  .bp3-button-group.bp3-minimal .bp3-button{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-button-group.bp3-minimal .bp3-button:hover{
      background:rgba(167, 182, 194, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026;
      text-decoration:none; }
    .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
      background:rgba(115, 134, 148, 0.3);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#182026; }
    .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
      background:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed; }
      .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button-group.bp3-minimal .bp3-button{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:inherit; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
        background:none;
        color:rgba(167, 182, 194, 0.6);
        cursor:not-allowed; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
      color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
      color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button-group .bp3-popover-wrapper,
  .bp3-button-group .bp3-popover-target{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button-group .bp3-button.bp3-fill,
  .bp3-button-group.bp3-fill .bp3-button:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-vertical{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    vertical-align:top; }
    .bp3-button-group.bp3-vertical.bp3-fill{
      height:100%;
      width:unset; }
    .bp3-button-group.bp3-vertical .bp3-button{
      margin-right:0 !important;
      width:100%; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:first-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:first-child{
      border-radius:3px 3px 0 0; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:last-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:last-child{
      border-radius:0 0 3px 3px; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:not(:last-child){
      margin-bottom:-1px; }
  .bp3-button-group.bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    margin-right:1px; }
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-button:not(:last-child){
    margin-bottom:1px; }
.bp3-callout{
  font-size:14px;
  line-height:1.5;
  background-color:rgba(138, 155, 168, 0.15);
  border-radius:3px;
  padding:10px 12px 9px;
  position:relative;
  width:100%; }
  .bp3-callout[class*="bp3-icon-"]{
    padding-left:40px; }
    .bp3-callout[class*="bp3-icon-"]::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout.bp3-callout-icon{
    padding-left:40px; }
    .bp3-callout.bp3-callout-icon > .bp3-icon:first-child{
      color:#5c7080;
      left:10px;
      position:absolute;
      top:10px; }
  .bp3-callout .bp3-heading{
    line-height:20px;
    margin-bottom:5px;
    margin-top:0; }
    .bp3-callout .bp3-heading:last-child{
      margin-bottom:0; }
  .bp3-dark .bp3-callout{
    background-color:rgba(138, 155, 168, 0.2); }
    .bp3-dark .bp3-callout[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
  .bp3-callout.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15); }
    .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-primary .bp3-heading{
      color:#106ba3; }
    .bp3-dark .bp3-callout.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-primary .bp3-heading{
        color:#48aff0; }
  .bp3-callout.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15); }
    .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-success .bp3-heading{
      color:#0d8050; }
    .bp3-dark .bp3-callout.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-success .bp3-heading{
        color:#3dcc91; }
  .bp3-callout.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15); }
    .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-warning .bp3-heading{
      color:#bf7326; }
    .bp3-dark .bp3-callout.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-warning .bp3-heading{
        color:#ffb366; }
  .bp3-callout.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15); }
    .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-danger .bp3-heading{
      color:#c23030; }
    .bp3-dark .bp3-callout.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-danger .bp3-heading{
        color:#ff7373; }
  .bp3-running-text .bp3-callout{
    margin:20px 0; }
.bp3-card{
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
  padding:20px;
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-card.bp3-dark,
  .bp3-dark .bp3-card{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-0{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }
  .bp3-elevation-0.bp3-dark,
  .bp3-dark .bp3-elevation-0{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-1{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-1.bp3-dark,
  .bp3-dark .bp3-elevation-1{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-elevation-2{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-2.bp3-dark,
  .bp3-dark .bp3-elevation-2{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4); }

.bp3-elevation-3{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-3.bp3-dark,
  .bp3-dark .bp3-elevation-3{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-elevation-4{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-4.bp3-dark,
  .bp3-dark .bp3-elevation-4{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:hover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  cursor:pointer; }
  .bp3-card.bp3-interactive:hover.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:active{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  opacity:0.9;
  -webkit-transition-duration:0;
          transition-duration:0; }
  .bp3-card.bp3-interactive:active.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-collapse{
  height:0;
  overflow-y:hidden;
  -webkit-transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-collapse .bp3-collapse-body{
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-collapse .bp3-collapse-body[aria-hidden="true"]{
      display:none; }

.bp3-context-menu .bp3-popover-target{
  display:block; }

.bp3-context-menu-popover-target{
  position:fixed; }

.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-dialog-container{
  opacity:1;
  -webkit-transform:scale(1);
          transform:scale(1);
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  min-height:100%;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  width:100%; }
  .bp3-dialog-container.bp3-overlay-enter > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5); }
  .bp3-dialog-container.bp3-overlay-enter-active > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear-active > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-dialog-container.bp3-overlay-exit > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-dialog-container.bp3-overlay-exit-active > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }

.bp3-dialog{
  background:#ebf1f5;
  border-radius:6px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:30px 0;
  padding-bottom:20px;
  pointer-events:all;
  -webkit-user-select:text;
     -moz-user-select:text;
      -ms-user-select:text;
          user-select:text;
  width:500px; }
  .bp3-dialog:focus{
    outline:0; }
  .bp3-dialog.bp3-dark,
  .bp3-dark .bp3-dialog{
    background:#293742;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-dialog-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background:#ffffff;
  border-radius:6px 6px 0 0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding-left:20px;
  padding-right:5px;
  z-index:30; }
  .bp3-dialog-header .bp3-icon-large,
  .bp3-dialog-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-dialog-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-dialog-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-dialog-header{
    background:#30404d;
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-dialog-header .bp3-icon-large,
    .bp3-dark .bp3-dialog-header .bp3-icon{
      color:#a7b6c2; }

.bp3-dialog-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  margin:20px; }

.bp3-dialog-footer{
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  margin:0 20px; }

.bp3-dialog-footer-actions{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:end;
      -ms-flex-pack:end;
          justify-content:flex-end; }
  .bp3-dialog-footer-actions .bp3-button{
    margin-left:10px; }
.bp3-multistep-dialog-panels{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }

.bp3-multistep-dialog-left-panel{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column; }
  .bp3-dark .bp3-multistep-dialog-left-panel{
    background:#202b33; }

.bp3-multistep-dialog-right-panel{
  background-color:#f5f8fa;
  border-left:1px solid rgba(16, 22, 26, 0.15);
  border-radius:0 0 6px 0;
  -webkit-box-flex:3;
      -ms-flex:3;
          flex:3;
  min-width:0; }
  .bp3-dark .bp3-multistep-dialog-right-panel{
    background-color:#293742;
    border-left:1px solid rgba(16, 22, 26, 0.4); }

.bp3-multistep-dialog-footer{
  background-color:#ffffff;
  border-radius:0 0 6px 0;
  border-top:1px solid rgba(16, 22, 26, 0.15);
  padding:10px; }
  .bp3-dark .bp3-multistep-dialog-footer{
    background:#30404d;
    border-top:1px solid rgba(16, 22, 26, 0.4); }

.bp3-dialog-step-container{
  background-color:#f5f8fa;
  border-bottom:1px solid rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-dialog-step-container{
    background:#293742;
    border-bottom:1px solid rgba(16, 22, 26, 0.4); }
  .bp3-dialog-step-container.bp3-dialog-step-viewed{
    background-color:#ffffff; }
    .bp3-dark .bp3-dialog-step-container.bp3-dialog-step-viewed{
      background:#30404d; }

.bp3-dialog-step{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#f5f8fa;
  border-radius:6px;
  cursor:not-allowed;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:4px;
  padding:6px 14px; }
  .bp3-dark .bp3-dialog-step{
    background:#293742; }
  .bp3-dialog-step-viewed .bp3-dialog-step{
    background-color:#ffffff;
    cursor:pointer; }
    .bp3-dark .bp3-dialog-step-viewed .bp3-dialog-step{
      background:#30404d; }
  .bp3-dialog-step:hover{
    background-color:#f5f8fa; }
    .bp3-dark .bp3-dialog-step:hover{
      background:#293742; }

.bp3-dialog-step-icon{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:rgba(92, 112, 128, 0.6);
  border-radius:50%;
  color:#ffffff;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:25px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  width:25px; }
  .bp3-dark .bp3-dialog-step-icon{
    background-color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#2b95d6; }
  .bp3-dialog-step-viewed .bp3-dialog-step-icon{
    background-color:#8a9ba8; }

.bp3-dialog-step-title{
  color:rgba(92, 112, 128, 0.6);
  -webkit-box-flex:1;
      -ms-flex:1;
          flex:1;
  padding-left:10px; }
  .bp3-dark .bp3-dialog-step-title{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-active.bp3-dialog-step-viewed .bp3-dialog-step-title{
    color:#2b95d6; }
  .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
    color:#182026; }
    .bp3-dark .bp3-dialog-step-viewed:not(.bp3-active) .bp3-dialog-step-title{
      color:#f5f8fa; }
.bp3-drawer{
  background:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0;
  padding:0; }
  .bp3-drawer:focus{
    outline:0; }
  .bp3-drawer.bp3-position-top{
    height:50%;
    left:0;
    right:0;
    top:0; }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter, .bp3-drawer.bp3-position-top.bp3-overlay-appear{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%); }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter-active, .bp3-drawer.bp3-position-top.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit-active{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-bottom{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter-active, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-left{
    bottom:0;
    left:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter, .bp3-drawer.bp3-position-left.bp3-overlay-appear{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%); }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter-active, .bp3-drawer.bp3-position-left.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit-active{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-position-right{
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter, .bp3-drawer.bp3-position-right.bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter-active, .bp3-drawer.bp3-position-right.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right):not(.bp3-vertical){
    bottom:0;
    right:0;
    top:0;
    width:50%; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right).bp3-vertical{
    bottom:0;
    height:50%;
    left:0;
    right:0; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-delay:0;
              transition-delay:0;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-drawer.bp3-dark,
  .bp3-dark .bp3-drawer{
    background:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }

.bp3-drawer-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border-radius:0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  min-height:40px;
  padding:5px;
  padding-left:20px;
  position:relative; }
  .bp3-drawer-header .bp3-icon-large,
  .bp3-drawer-header .bp3-icon{
    color:#5c7080;
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px; }
  .bp3-drawer-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:inherit;
    margin:0; }
    .bp3-drawer-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-drawer-header{
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-drawer-header .bp3-icon-large,
    .bp3-dark .bp3-drawer-header .bp3-icon{
      color:#a7b6c2; }

.bp3-drawer-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  line-height:18px;
  overflow:auto; }

.bp3-drawer-footer{
  -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  padding:10px 20px;
  position:relative; }
  .bp3-dark .bp3-drawer-footer{
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4); }
.bp3-editable-text{
  cursor:text;
  display:inline-block;
  max-width:100%;
  position:relative;
  vertical-align:top;
  white-space:nowrap; }
  .bp3-editable-text::before{
    bottom:-3px;
    left:-3px;
    position:absolute;
    right:-3px;
    top:-3px;
    border-radius:3px;
    content:"";
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#137cbd; }
  .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4); }
  .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#0f9960; }
  .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4); }
  .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#d9822b; }
  .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4); }
  .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#db3737; }
  .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4); }
  .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15); }
  .bp3-dark .bp3-editable-text.bp3-editable-text-editing::before{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#48aff0; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4);
            box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#3dcc91; }
  .bp3-dark .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4);
            box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#ffb366; }
  .bp3-dark .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4);
            box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#ff7373; }
  .bp3-dark .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4);
            box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-editable-text-input,
.bp3-editable-text-content{
  color:inherit;
  display:inherit;
  font:inherit;
  letter-spacing:inherit;
  max-width:inherit;
  min-width:inherit;
  position:relative;
  resize:none;
  text-transform:inherit;
  vertical-align:top; }

.bp3-editable-text-input{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0;
  white-space:pre-wrap;
  width:100%; }
  .bp3-editable-text-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-editable-text-input:focus{
    outline:none; }
  .bp3-editable-text-input::-ms-clear{
    display:none; }

.bp3-editable-text-content{
  overflow:hidden;
  padding-right:2px;
  text-overflow:ellipsis;
  white-space:pre; }
  .bp3-editable-text-editing > .bp3-editable-text-content{
    left:0;
    position:absolute;
    visibility:hidden; }
  .bp3-editable-text-placeholder > .bp3-editable-text-content{
    color:rgba(92, 112, 128, 0.6); }
    .bp3-dark .bp3-editable-text-placeholder > .bp3-editable-text-content{
      color:rgba(167, 182, 194, 0.6); }

.bp3-editable-text.bp3-multiline{
  display:block; }
  .bp3-editable-text.bp3-multiline .bp3-editable-text-content{
    overflow:auto;
    white-space:pre-wrap;
    word-wrap:break-word; }
.bp3-divider{
  border-bottom:1px solid rgba(16, 22, 26, 0.15);
  border-right:1px solid rgba(16, 22, 26, 0.15);
  margin:5px; }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-control-group{
  -webkit-transform:translateZ(0);
          transform:translateZ(0);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:stretch;
      -ms-flex-align:stretch;
          align-items:stretch; }
  .bp3-control-group > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select,
  .bp3-control-group .bp3-input,
  .bp3-control-group .bp3-select{
    position:relative; }
  .bp3-control-group .bp3-input{
    border-radius:inherit;
    z-index:2; }
    .bp3-control-group .bp3-input:focus{
      border-radius:3px;
      z-index:14; }
    .bp3-control-group .bp3-input[class*="bp3-intent"]{
      z-index:13; }
      .bp3-control-group .bp3-input[class*="bp3-intent"]:focus{
        z-index:15; }
    .bp3-control-group .bp3-input[readonly], .bp3-control-group .bp3-input:disabled, .bp3-control-group .bp3-input.bp3-disabled{
      z-index:1; }
  .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input{
    z-index:13; }
    .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input:focus{
      z-index:15; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select select,
  .bp3-control-group .bp3-select select{
    -webkit-transform:translateZ(0);
            transform:translateZ(0);
    border-radius:inherit;
    z-index:4; }
    .bp3-control-group .bp3-button:focus,
    .bp3-control-group .bp3-html-select select:focus,
    .bp3-control-group .bp3-select select:focus{
      z-index:5; }
    .bp3-control-group .bp3-button:hover,
    .bp3-control-group .bp3-html-select select:hover,
    .bp3-control-group .bp3-select select:hover{
      z-index:6; }
    .bp3-control-group .bp3-button:active,
    .bp3-control-group .bp3-html-select select:active,
    .bp3-control-group .bp3-select select:active{
      z-index:7; }
    .bp3-control-group .bp3-button[readonly], .bp3-control-group .bp3-button:disabled, .bp3-control-group .bp3-button.bp3-disabled,
    .bp3-control-group .bp3-html-select select[readonly],
    .bp3-control-group .bp3-html-select select:disabled,
    .bp3-control-group .bp3-html-select select.bp3-disabled,
    .bp3-control-group .bp3-select select[readonly],
    .bp3-control-group .bp3-select select:disabled,
    .bp3-control-group .bp3-select select.bp3-disabled{
      z-index:3; }
    .bp3-control-group .bp3-button[class*="bp3-intent"],
    .bp3-control-group .bp3-html-select select[class*="bp3-intent"],
    .bp3-control-group .bp3-select select[class*="bp3-intent"]{
      z-index:9; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:focus{
        z-index:10; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:hover{
        z-index:11; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:active{
        z-index:12; }
      .bp3-control-group .bp3-button[class*="bp3-intent"][readonly], .bp3-control-group .bp3-button[class*="bp3-intent"]:disabled, .bp3-control-group .bp3-button[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"].bp3-disabled{
        z-index:8; }
  .bp3-control-group .bp3-input-group > .bp3-icon,
  .bp3-control-group .bp3-input-group > .bp3-button,
  .bp3-control-group .bp3-input-group > .bp3-input-left-container,
  .bp3-control-group .bp3-input-group > .bp3-input-action{
    z-index:16; }
  .bp3-control-group .bp3-select::after,
  .bp3-control-group .bp3-html-select::after,
  .bp3-control-group .bp3-select > .bp3-icon,
  .bp3-control-group .bp3-html-select > .bp3-icon{
    z-index:17; }
  .bp3-control-group .bp3-select:focus-within{
    z-index:5; }
  .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:-1px; }
  .bp3-control-group:not(.bp3-vertical) > .bp3-divider:not(:first-child){
    margin-left:6px; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > *:not(.bp3-divider){
    margin-right:0; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > .bp3-button + .bp3-button{
    margin-left:1px; }
  .bp3-control-group .bp3-popover-wrapper,
  .bp3-control-group .bp3-popover-target{
    border-radius:inherit; }
  .bp3-control-group > :first-child{
    border-radius:3px 0 0 3px; }
  .bp3-control-group > :last-child{
    border-radius:0 3px 3px 0;
    margin-right:0; }
  .bp3-control-group > :only-child{
    border-radius:3px;
    margin-right:0; }
  .bp3-control-group .bp3-input-group .bp3-button{
    border-radius:3px; }
  .bp3-control-group .bp3-numeric-input:not(:first-child) .bp3-input-group{
    border-bottom-left-radius:0;
    border-top-left-radius:0; }
  .bp3-control-group.bp3-fill{
    width:100%; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-fill > *:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-vertical{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-control-group.bp3-vertical > *{
      margin-top:-1px; }
    .bp3-control-group.bp3-vertical > :first-child{
      border-radius:3px 3px 0 0;
      margin-top:0; }
    .bp3-control-group.bp3-vertical > :last-child{
      border-radius:0 0 3px 3px; }
.bp3-control{
  cursor:pointer;
  display:block;
  margin-bottom:10px;
  position:relative;
  text-transform:none; }
  .bp3-control input:checked ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control:hover input:checked ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control:not(.bp3-align-right){
    padding-left:26px; }
    .bp3-control:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-26px; }
  .bp3-control.bp3-align-right{
    padding-right:26px; }
    .bp3-control.bp3-align-right .bp3-control-indicator{
      margin-right:-26px; }
  .bp3-control.bp3-disabled{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-control.bp3-inline{
    display:inline-block;
    margin-right:20px; }
  .bp3-control input{
    left:0;
    opacity:0;
    position:absolute;
    top:0;
    z-index:-1; }
  .bp3-control .bp3-control-indicator{
    background-clip:padding-box;
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    border:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    cursor:pointer;
    display:inline-block;
    font-size:16px;
    height:1em;
    margin-right:10px;
    margin-top:-3px;
    position:relative;
    -webkit-user-select:none;
       -moz-user-select:none;
        -ms-user-select:none;
            user-select:none;
    vertical-align:middle;
    width:1em; }
    .bp3-control .bp3-control-indicator::before{
      content:"";
      display:block;
      height:1em;
      width:1em; }
  .bp3-control:hover .bp3-control-indicator{
    background-color:#ebf1f5; }
  .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
    background:#d8e1e8;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    cursor:not-allowed; }
  .bp3-control input:focus ~ .bp3-control-indicator{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:2px;
    -moz-outline-radius:6px; }
  .bp3-control.bp3-align-right .bp3-control-indicator{
    float:right;
    margin-left:10px;
    margin-top:1px; }
  .bp3-control.bp3-large{
    font-size:16px; }
    .bp3-control.bp3-large:not(.bp3-align-right){
      padding-left:30px; }
      .bp3-control.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-30px; }
    .bp3-control.bp3-large.bp3-align-right{
      padding-right:30px; }
      .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-right:-30px; }
    .bp3-control.bp3-large .bp3-control-indicator{
      font-size:20px; }
    .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-top:0; }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    color:#ffffff; }
  .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background:#0e5a8a;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    background-color:#106ba3;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    background-color:#0e5a8a;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-control.bp3-checkbox .bp3-control-indicator{
    border-radius:3px; }
  .bp3-control.bp3-checkbox input:checked ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M12 5c-.28 0-.53.11-.71.29L7 9.59l-2.29-2.3a1.003 1.003 0 00-1.42 1.42l3 3c.18.18.43.29.71.29s.53-.11.71-.29l5-5A1.003 1.003 0 0012 5z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 7H5c-.55 0-1 .45-1 1s.45 1 1 1h6c.55 0 1-.45 1-1s-.45-1-1-1z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-radio .bp3-control-indicator{
    border-radius:50%; }
  .bp3-control.bp3-radio input:checked ~ .bp3-control-indicator::before{
    background-image:radial-gradient(#ffffff, #ffffff 28%, transparent 32%); }
  .bp3-control.bp3-radio input:checked:disabled ~ .bp3-control-indicator::before{
    opacity:0.5; }
  .bp3-control.bp3-radio input:focus ~ .bp3-control-indicator{
    -moz-outline-radius:16px; }
  .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(167, 182, 194, 0.5); }
  .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(115, 134, 148, 0.5); }
  .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(92, 112, 128, 0.5); }
  .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5); }
    .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5); }
    .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch:not(.bp3-align-right){
    padding-left:38px; }
    .bp3-control.bp3-switch:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-38px; }
  .bp3-control.bp3-switch.bp3-align-right{
    padding-right:38px; }
    .bp3-control.bp3-switch.bp3-align-right .bp3-control-indicator{
      margin-right:-38px; }
  .bp3-control.bp3-switch .bp3-control-indicator{
    border:none;
    border-radius:1.75em;
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    min-width:1.75em;
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:auto; }
    .bp3-control.bp3-switch .bp3-control-indicator::before{
      background:#ffffff;
      border-radius:50%;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
      height:calc(1em - 4px);
      left:0;
      margin:2px;
      position:absolute;
      -webkit-transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      width:calc(1em - 4px); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    left:calc(100% - 1em); }
  .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right){
    padding-left:45px; }
    .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-45px; }
  .bp3-control.bp3-switch.bp3-large.bp3-align-right{
    padding-right:45px; }
    .bp3-control.bp3-switch.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-right:-45px; }
  .bp3-dark .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.7); }
  .bp3-dark .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.9); }
  .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(57, 75, 89, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-dark .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-dark .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch .bp3-control-indicator::before{
    background:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-control.bp3-switch .bp3-switch-inner-text{
    font-size:0.7em;
    text-align:center; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:first-child{
    line-height:0;
    margin-left:0.5em;
    margin-right:1.2em;
    visibility:hidden; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:last-child{
    line-height:1em;
    margin-left:1.2em;
    margin-right:0.5em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:first-child{
    line-height:1em;
    visibility:visible; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:last-child{
    line-height:0;
    visibility:hidden; }
  .bp3-dark .bp3-control{
    color:#f5f8fa; }
    .bp3-dark .bp3-control.bp3-disabled{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-control .bp3-control-indicator{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-control:hover .bp3-control-indicator{
      background-color:#30404d; }
    .bp3-dark .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
      background:#202b33;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-control input:disabled ~ .bp3-control-indicator{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      cursor:not-allowed; }
    .bp3-dark .bp3-control.bp3-checkbox input:disabled:checked ~ .bp3-control-indicator, .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      color:rgba(167, 182, 194, 0.6); }
.bp3-file-input{
  cursor:pointer;
  display:inline-block;
  height:30px;
  position:relative; }
  .bp3-file-input input{
    margin:0;
    min-width:200px;
    opacity:0; }
    .bp3-file-input input:disabled + .bp3-file-upload-input,
    .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
      background:rgba(206, 217, 224, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      resize:none; }
      .bp3-file-input input:disabled + .bp3-file-upload-input::after,
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(92, 112, 128, 0.6);
        cursor:not-allowed;
        outline:none; }
        .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active:hover,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
      .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input, .bp3-dark
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
        background:rgba(57, 75, 89, 0.5);
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after, .bp3-dark
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
          background-color:rgba(57, 75, 89, 0.5);
          background-image:none;
          -webkit-box-shadow:none;
                  box-shadow:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-dark
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active{
            background:rgba(57, 75, 89, 0.7); }
  .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#182026; }
  .bp3-dark .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#f5f8fa; }
  .bp3-file-input.bp3-fill{
    width:100%; }
  .bp3-file-input.bp3-large,
  .bp3-large .bp3-file-input{
    height:40px; }
  .bp3-file-input .bp3-file-upload-input-custom-text::after{
    content:attr(bp3-button-text); }

.bp3-file-upload-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle;
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:rgba(92, 112, 128, 0.6);
  left:0;
  padding-right:80px;
  position:absolute;
  right:0;
  top:0;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-file-upload-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-file-upload-input:focus, .bp3-file-upload-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-file-upload-input[type="search"], .bp3-file-upload-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-file-upload-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-file-upload-input:disabled, .bp3-file-upload-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-file-upload-input::after{
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    color:#182026;
    min-height:24px;
    min-width:24px;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    border-radius:3px;
    content:"Browse";
    line-height:24px;
    margin:3px;
    position:absolute;
    right:0;
    text-align:center;
    top:0;
    width:70px; }
    .bp3-file-upload-input::after:hover{
      background-clip:padding-box;
      background-color:#ebf1f5;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
    .bp3-file-upload-input::after:active, .bp3-file-upload-input::after.bp3-active{
      background-color:#d8e1e8;
      background-image:none;
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-file-upload-input::after:disabled, .bp3-file-upload-input::after.bp3-disabled{
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(92, 112, 128, 0.6);
      cursor:not-allowed;
      outline:none; }
      .bp3-file-upload-input::after:disabled.bp3-active, .bp3-file-upload-input::after:disabled.bp3-active:hover, .bp3-file-upload-input::after.bp3-disabled.bp3-active, .bp3-file-upload-input::after.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-file-upload-input:hover::after{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-file-upload-input:active::after{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-large .bp3-file-upload-input{
    font-size:16px;
    height:40px;
    line-height:40px;
    padding-right:95px; }
    .bp3-large .bp3-file-upload-input[type="search"], .bp3-large .bp3-file-upload-input.bp3-round{
      padding:0 15px; }
    .bp3-large .bp3-file-upload-input::after{
      min-height:30px;
      min-width:30px;
      line-height:30px;
      margin:5px;
      width:85px; }
  .bp3-dark .bp3-file-upload-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:disabled, .bp3-dark .bp3-file-upload-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::after{
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover, .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover{
        background-color:#30404d;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        background-color:#202b33;
        background-image:none;
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
      .bp3-dark .bp3-file-upload-input::after:disabled, .bp3-dark .bp3-file-upload-input::after.bp3-disabled{
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-upload-input::after:disabled.bp3-active, .bp3-dark .bp3-file-upload-input::after.bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-file-upload-input::after .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
    .bp3-dark .bp3-file-upload-input:hover::after{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:active::after{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
.bp3-file-upload-input::after{
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
.bp3-form-group{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0 0 15px; }
  .bp3-form-group label.bp3-label{
    margin-bottom:5px; }
  .bp3-form-group .bp3-control{
    margin-top:7px; }
  .bp3-form-group .bp3-form-helper-text{
    color:#5c7080;
    font-size:12px;
    margin-top:5px; }
  .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#106ba3; }
  .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#0d8050; }
  .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#bf7326; }
  .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#c23030; }
  .bp3-form-group.bp3-inline{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row; }
    .bp3-form-group.bp3-inline.bp3-large label.bp3-label{
      line-height:40px;
      margin:0 10px 0 0; }
    .bp3-form-group.bp3-inline label.bp3-label{
      line-height:30px;
      margin:0 10px 0 0; }
  .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-dark .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#48aff0; }
  .bp3-dark .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#3dcc91; }
  .bp3-dark .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#ffb366; }
  .bp3-dark .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#ff7373; }
  .bp3-dark .bp3-form-group .bp3-form-helper-text{
    color:#a7b6c2; }
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(167, 182, 194, 0.6) !important; }
.bp3-input-group{
  display:block;
  position:relative; }
  .bp3-input-group .bp3-input{
    position:relative;
    width:100%; }
    .bp3-input-group .bp3-input:not(:first-child){
      padding-left:30px; }
    .bp3-input-group .bp3-input:not(:last-child){
      padding-right:30px; }
  .bp3-input-group .bp3-input-action,
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-button,
  .bp3-input-group > .bp3-icon{
    position:absolute;
    top:0; }
    .bp3-input-group .bp3-input-action:first-child,
    .bp3-input-group > .bp3-input-left-container:first-child,
    .bp3-input-group > .bp3-button:first-child,
    .bp3-input-group > .bp3-icon:first-child{
      left:0; }
    .bp3-input-group .bp3-input-action:last-child,
    .bp3-input-group > .bp3-input-left-container:last-child,
    .bp3-input-group > .bp3-button:last-child,
    .bp3-input-group > .bp3-icon:last-child{
      right:0; }
  .bp3-input-group .bp3-button{
    min-height:24px;
    min-width:24px;
    margin:3px;
    padding:0 7px; }
    .bp3-input-group .bp3-button:empty{
      padding:0; }
  .bp3-input-group > .bp3-input-left-container,
  .bp3-input-group > .bp3-icon{
    z-index:1; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon{
    color:#5c7080; }
    .bp3-input-group > .bp3-input-left-container > .bp3-icon:empty,
    .bp3-input-group > .bp3-icon:empty{
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased; }
  .bp3-input-group > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group > .bp3-icon,
  .bp3-input-group .bp3-input-action > .bp3-spinner{
    margin:7px; }
  .bp3-input-group .bp3-tag{
    margin:5px; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus),
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
    color:#5c7080; }
    .bp3-dark .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus), .bp3-dark
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
      color:#a7b6c2; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large{
      color:#5c7080; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled,
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled{
    color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-large{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-input-group.bp3-disabled{
    cursor:not-allowed; }
    .bp3-input-group.bp3-disabled .bp3-icon{
      color:rgba(92, 112, 128, 0.6); }
  .bp3-input-group.bp3-large .bp3-button{
    min-height:30px;
    min-width:30px;
    margin:5px; }
  .bp3-input-group.bp3-large > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-large > .bp3-icon,
  .bp3-input-group.bp3-large .bp3-input-action > .bp3-spinner{
    margin:12px; }
  .bp3-input-group.bp3-large .bp3-input{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input-group.bp3-large .bp3-input[type="search"], .bp3-input-group.bp3-large .bp3-input.bp3-round{
      padding:0 15px; }
    .bp3-input-group.bp3-large .bp3-input:not(:first-child){
      padding-left:40px; }
    .bp3-input-group.bp3-large .bp3-input:not(:last-child){
      padding-right:40px; }
  .bp3-input-group.bp3-small .bp3-button{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small .bp3-tag{
    min-height:20px;
    min-width:20px;
    margin:2px; }
  .bp3-input-group.bp3-small > .bp3-input-left-container > .bp3-icon,
  .bp3-input-group.bp3-small > .bp3-icon,
  .bp3-input-group.bp3-small .bp3-input-action > .bp3-spinner{
    margin:4px; }
  .bp3-input-group.bp3-small .bp3-input{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input-group.bp3-small .bp3-input[type="search"], .bp3-input-group.bp3-small .bp3-input.bp3-round{
      padding:0 12px; }
    .bp3-input-group.bp3-small .bp3-input:not(:first-child){
      padding-left:24px; }
    .bp3-input-group.bp3-small .bp3-input:not(:last-child){
      padding-right:24px; }
  .bp3-input-group.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-input-group.bp3-round .bp3-button,
  .bp3-input-group.bp3-round .bp3-input,
  .bp3-input-group.bp3-round .bp3-tag{
    border-radius:30px; }
  .bp3-dark .bp3-input-group .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-input-group.bp3-disabled .bp3-icon{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-input-group.bp3-intent-primary .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input-group.bp3-intent-primary .bp3-input:disabled, .bp3-input-group.bp3-intent-primary .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-primary > .bp3-icon{
    color:#106ba3; }
    .bp3-dark .bp3-input-group.bp3-intent-primary > .bp3-icon{
      color:#48aff0; }
  .bp3-input-group.bp3-intent-success .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input-group.bp3-intent-success .bp3-input:disabled, .bp3-input-group.bp3-intent-success .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-success > .bp3-icon{
    color:#0d8050; }
    .bp3-dark .bp3-input-group.bp3-intent-success > .bp3-icon{
      color:#3dcc91; }
  .bp3-input-group.bp3-intent-warning .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input-group.bp3-intent-warning .bp3-input:disabled, .bp3-input-group.bp3-intent-warning .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-warning > .bp3-icon{
    color:#bf7326; }
    .bp3-dark .bp3-input-group.bp3-intent-warning > .bp3-icon{
      color:#ffb366; }
  .bp3-input-group.bp3-intent-danger .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input-group.bp3-intent-danger .bp3-input:disabled, .bp3-input-group.bp3-intent-danger .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-danger > .bp3-icon{
    color:#c23030; }
    .bp3-dark .bp3-input-group.bp3-intent-danger > .bp3-icon{
      color:#ff7373; }
.bp3-input{
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  background:#ffffff;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  color:#182026;
  font-size:14px;
  font-weight:400;
  height:30px;
  line-height:30px;
  outline:none;
  padding:0 10px;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  vertical-align:middle; }
  .bp3-input::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input:focus, .bp3-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-input[type="search"], .bp3-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-input:disabled, .bp3-input.bp3-disabled{
    background:rgba(206, 217, 224, 0.5);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    resize:none; }
  .bp3-input.bp3-large{
    font-size:16px;
    height:40px;
    line-height:40px; }
    .bp3-input.bp3-large[type="search"], .bp3-input.bp3-large.bp3-round{
      padding:0 15px; }
  .bp3-input.bp3-small{
    font-size:12px;
    height:24px;
    line-height:24px;
    padding-left:8px;
    padding-right:8px; }
    .bp3-input.bp3-small[type="search"], .bp3-input.bp3-small.bp3-round{
      padding:0 12px; }
  .bp3-input.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-dark .bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input:disabled, .bp3-dark .bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-input.bp3-intent-primary{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input.bp3-intent-primary:disabled, .bp3-input.bp3-intent-primary.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-dark .bp3-input.bp3-intent-primary:disabled, .bp3-dark .bp3-input.bp3-intent-primary.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-success{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input.bp3-intent-success:disabled, .bp3-input.bp3-intent-success.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-success{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-dark .bp3-input.bp3-intent-success:disabled, .bp3-dark .bp3-input.bp3-intent-success.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-warning{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input.bp3-intent-warning:disabled, .bp3-input.bp3-intent-warning.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-dark .bp3-input.bp3-intent-warning:disabled, .bp3-dark .bp3-input.bp3-intent-warning.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-danger{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input.bp3-intent-danger:disabled, .bp3-input.bp3-intent-danger.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-dark .bp3-input.bp3-intent-danger:disabled, .bp3-dark .bp3-input.bp3-intent-danger.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input::-ms-clear{
    display:none; }
textarea.bp3-input{
  max-width:100%;
  padding:10px; }
  textarea.bp3-input, textarea.bp3-input.bp3-large, textarea.bp3-input.bp3-small{
    height:auto;
    line-height:inherit; }
  textarea.bp3-input.bp3-small{
    padding:8px; }
  .bp3-dark textarea.bp3-input{
    background:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark textarea.bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input:disabled, .bp3-dark textarea.bp3-input.bp3-disabled{
      background:rgba(57, 75, 89, 0.5);
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
label.bp3-label{
  display:block;
  margin-bottom:15px;
  margin-top:0; }
  label.bp3-label .bp3-html-select,
  label.bp3-label .bp3-input,
  label.bp3-label .bp3-select,
  label.bp3-label .bp3-slider,
  label.bp3-label .bp3-popover-wrapper{
    display:block;
    margin-top:5px;
    text-transform:none; }
  label.bp3-label .bp3-button-group{
    margin-top:5px; }
  label.bp3-label .bp3-select select,
  label.bp3-label .bp3-html-select select{
    font-weight:400;
    vertical-align:top;
    width:100%; }
  label.bp3-label.bp3-disabled,
  label.bp3-label.bp3-disabled .bp3-text-muted{
    color:rgba(92, 112, 128, 0.6); }
  label.bp3-label.bp3-inline{
    line-height:30px; }
    label.bp3-label.bp3-inline .bp3-html-select,
    label.bp3-label.bp3-inline .bp3-input,
    label.bp3-label.bp3-inline .bp3-input-group,
    label.bp3-label.bp3-inline .bp3-select,
    label.bp3-label.bp3-inline .bp3-popover-wrapper{
      display:inline-block;
      margin:0 0 0 5px;
      vertical-align:top; }
    label.bp3-label.bp3-inline .bp3-button-group{
      margin:0 0 0 5px; }
    label.bp3-label.bp3-inline .bp3-input-group .bp3-input{
      margin-left:0; }
    label.bp3-label.bp3-inline.bp3-large{
      line-height:40px; }
  label.bp3-label:not(.bp3-inline) .bp3-popover-target{
    display:block; }
  .bp3-dark label.bp3-label{
    color:#f5f8fa; }
    .bp3-dark label.bp3-label.bp3-disabled,
    .bp3-dark label.bp3-label.bp3-disabled .bp3-text-muted{
      color:rgba(167, 182, 194, 0.6); }
.bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button{
  -webkit-box-flex:1;
      -ms-flex:1 1 14px;
          flex:1 1 14px;
  min-height:0;
  padding:0;
  width:30px; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:first-child{
    border-radius:0 3px 0 0; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:last-child{
    border-radius:0 0 3px 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:first-child{
  border-radius:3px 0 0 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:last-child{
  border-radius:0 0 0 3px; }

.bp3-numeric-input.bp3-large .bp3-button-group.bp3-vertical > .bp3-button{
  width:40px; }

form{
  display:block; }
.bp3-html-select select,
.bp3-select select{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  font-size:14px;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  padding:5px 10px;
  text-align:left;
  vertical-align:middle;
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  -moz-appearance:none;
  -webkit-appearance:none;
  border-radius:3px;
  height:30px;
  padding:0 25px 0 10px;
  width:100%; }
  .bp3-html-select select > *, .bp3-select select > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-html-select select > .bp3-fill, .bp3-select select > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-html-select select::before,
  .bp3-select select::before, .bp3-html-select select > *, .bp3-select select > *{
    margin-right:7px; }
  .bp3-html-select select:empty::before,
  .bp3-select select:empty::before,
  .bp3-html-select select > :last-child,
  .bp3-select select > :last-child{
    margin-right:0; }
  .bp3-html-select select:hover,
  .bp3-select select:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-html-select select:active,
  .bp3-select select:active, .bp3-html-select select.bp3-active,
  .bp3-select select.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-html-select select:disabled,
  .bp3-select select:disabled, .bp3-html-select select.bp3-disabled,
  .bp3-select select.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-html-select select:disabled.bp3-active,
    .bp3-select select:disabled.bp3-active, .bp3-html-select select:disabled.bp3-active:hover,
    .bp3-select select:disabled.bp3-active:hover, .bp3-html-select select.bp3-disabled.bp3-active,
    .bp3-select select.bp3-disabled.bp3-active, .bp3-html-select select.bp3-disabled.bp3-active:hover,
    .bp3-select select.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }

.bp3-html-select.bp3-minimal select,
.bp3-select.bp3-minimal select{
  background:none;
  -webkit-box-shadow:none;
          box-shadow:none; }
  .bp3-html-select.bp3-minimal select:hover,
  .bp3-select.bp3-minimal select:hover{
    background:rgba(167, 182, 194, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026;
    text-decoration:none; }
  .bp3-html-select.bp3-minimal select:active,
  .bp3-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal select.bp3-active,
  .bp3-select.bp3-minimal select.bp3-active{
    background:rgba(115, 134, 148, 0.3);
    -webkit-box-shadow:none;
            box-shadow:none;
    color:#182026; }
  .bp3-html-select.bp3-minimal select:disabled,
  .bp3-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal select:disabled:hover,
  .bp3-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal select.bp3-disabled,
  .bp3-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal select.bp3-disabled:hover,
  .bp3-select.bp3-minimal select.bp3-disabled:hover{
    background:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
    .bp3-html-select.bp3-minimal select:disabled.bp3-active,
    .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active{
      background:rgba(115, 134, 148, 0.3); }
  .bp3-dark .bp3-html-select.bp3-minimal select, .bp3-html-select.bp3-minimal .bp3-dark select,
  .bp3-dark .bp3-select.bp3-minimal select, .bp3-select.bp3-minimal .bp3-dark select{
    background:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:inherit; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover, .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover{
      background:rgba(138, 155, 168, 0.15); }
    .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:rgba(138, 155, 168, 0.3);
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal .bp3-dark select:disabled,
    .bp3-dark .bp3-select.bp3-minimal select:disabled, .bp3-select.bp3-minimal .bp3-dark select:disabled, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select:disabled:hover, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover{
      background:none;
      color:rgba(167, 182, 194, 0.6);
      cursor:not-allowed; }
      .bp3-dark .bp3-html-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active{
        background:rgba(138, 155, 168, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-primary,
  .bp3-select.bp3-minimal select.bp3-intent-primary{
    color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover{
      background:rgba(19, 124, 189, 0.15);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:rgba(19, 124, 189, 0.3);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled{
      background:none;
      color:rgba(16, 107, 163, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active{
        background:rgba(19, 124, 189, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
      stroke:#106ba3; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary{
      color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.2);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(72, 175, 240, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-success,
  .bp3-select.bp3-minimal select.bp3-intent-success{
    color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover{
      background:rgba(15, 153, 96, 0.15);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:rgba(15, 153, 96, 0.3);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled{
      background:none;
      color:rgba(13, 128, 80, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active{
        background:rgba(15, 153, 96, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
      stroke:#0d8050; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success{
      color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.2);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(61, 204, 145, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-warning,
  .bp3-select.bp3-minimal select.bp3-intent-warning{
    color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover{
      background:rgba(217, 130, 43, 0.15);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:rgba(217, 130, 43, 0.3);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled{
      background:none;
      color:rgba(191, 115, 38, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active{
        background:rgba(217, 130, 43, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
      stroke:#bf7326; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning{
      color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.2);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(255, 179, 102, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-danger,
  .bp3-select.bp3-minimal select.bp3-intent-danger{
    color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover{
      background:rgba(219, 55, 55, 0.15);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:rgba(219, 55, 55, 0.3);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled{
      background:none;
      color:rgba(194, 48, 48, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active{
        background:rgba(219, 55, 55, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
      stroke:#c23030; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger{
      color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.2);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(255, 115, 115, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }

.bp3-html-select.bp3-large select,
.bp3-select.bp3-large select{
  font-size:16px;
  height:40px;
  padding-right:35px; }

.bp3-dark .bp3-html-select select, .bp3-dark .bp3-select select{
  background-color:#394b59;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
  color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover, .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    background-color:#202b33;
    background-image:none;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-html-select select:disabled, .bp3-dark .bp3-select select:disabled, .bp3-dark .bp3-html-select select.bp3-disabled, .bp3-dark .bp3-select select.bp3-disabled{
    background-color:rgba(57, 75, 89, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-html-select select:disabled.bp3-active, .bp3-dark .bp3-select select:disabled.bp3-active, .bp3-dark .bp3-html-select select.bp3-disabled.bp3-active, .bp3-dark .bp3-select select.bp3-disabled.bp3-active{
      background:rgba(57, 75, 89, 0.7); }
  .bp3-dark .bp3-html-select select .bp3-button-spinner .bp3-spinner-head, .bp3-dark .bp3-select select .bp3-button-spinner .bp3-spinner-head{
    background:rgba(16, 22, 26, 0.5);
    stroke:#8a9ba8; }

.bp3-html-select select:disabled,
.bp3-select select:disabled{
  background-color:rgba(206, 217, 224, 0.5);
  -webkit-box-shadow:none;
          box-shadow:none;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-html-select .bp3-icon,
.bp3-select .bp3-icon, .bp3-select::after{
  color:#5c7080;
  pointer-events:none;
  position:absolute;
  right:7px;
  top:7px; }
  .bp3-html-select .bp3-disabled.bp3-icon,
  .bp3-select .bp3-disabled.bp3-icon, .bp3-disabled.bp3-select::after{
    color:rgba(92, 112, 128, 0.6); }
.bp3-html-select,
.bp3-select{
  display:inline-block;
  letter-spacing:normal;
  position:relative;
  vertical-align:middle; }
  .bp3-html-select select::-ms-expand,
  .bp3-select select::-ms-expand{
    display:none; }
  .bp3-html-select .bp3-icon,
  .bp3-select .bp3-icon{
    color:#5c7080; }
    .bp3-html-select .bp3-icon:hover,
    .bp3-select .bp3-icon:hover{
      color:#182026; }
    .bp3-dark .bp3-html-select .bp3-icon, .bp3-dark
    .bp3-select .bp3-icon{
      color:#a7b6c2; }
      .bp3-dark .bp3-html-select .bp3-icon:hover, .bp3-dark
      .bp3-select .bp3-icon:hover{
        color:#f5f8fa; }
  .bp3-html-select.bp3-large::after,
  .bp3-html-select.bp3-large .bp3-icon,
  .bp3-select.bp3-large::after,
  .bp3-select.bp3-large .bp3-icon{
    right:12px;
    top:12px; }
  .bp3-html-select.bp3-fill,
  .bp3-html-select.bp3-fill select,
  .bp3-select.bp3-fill,
  .bp3-select.bp3-fill select{
    width:100%; }
  .bp3-dark .bp3-html-select option, .bp3-dark
  .bp3-select option{
    background-color:#30404d;
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select option:disabled, .bp3-dark
  .bp3-select option:disabled{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-html-select::after, .bp3-dark
  .bp3-select::after{
    color:#a7b6c2; }

.bp3-select::after{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  content:""; }
.bp3-running-text table, table.bp3-html-table{
  border-spacing:0;
  font-size:14px; }
  .bp3-running-text table th, table.bp3-html-table th,
  .bp3-running-text table td,
  table.bp3-html-table td{
    padding:11px;
    text-align:left;
    vertical-align:top; }
  .bp3-running-text table th, table.bp3-html-table th{
    color:#182026;
    font-weight:600; }
  
  .bp3-running-text table td,
  table.bp3-html-table td{
    color:#182026; }
  .bp3-running-text table tbody tr:first-child th, table.bp3-html-table tbody tr:first-child th,
  .bp3-running-text table tbody tr:first-child td,
  table.bp3-html-table tbody tr:first-child td,
  .bp3-running-text table tfoot tr:first-child th,
  table.bp3-html-table tfoot tr:first-child th,
  .bp3-running-text table tfoot tr:first-child td,
  table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-running-text table th, .bp3-running-text .bp3-dark table th, .bp3-dark table.bp3-html-table th{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table td, .bp3-running-text .bp3-dark table td, .bp3-dark table.bp3-html-table td{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table tbody tr:first-child th, .bp3-running-text .bp3-dark table tbody tr:first-child th, .bp3-dark table.bp3-html-table tbody tr:first-child th,
  .bp3-dark .bp3-running-text table tbody tr:first-child td,
  .bp3-running-text .bp3-dark table tbody tr:first-child td,
  .bp3-dark table.bp3-html-table tbody tr:first-child td,
  .bp3-dark .bp3-running-text table tfoot tr:first-child th,
  .bp3-running-text .bp3-dark table tfoot tr:first-child th,
  .bp3-dark table.bp3-html-table tfoot tr:first-child th,
  .bp3-dark .bp3-running-text table tfoot tr:first-child td,
  .bp3-running-text .bp3-dark table tfoot tr:first-child td,
  .bp3-dark table.bp3-html-table tfoot tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }

table.bp3-html-table.bp3-html-table-condensed th,
table.bp3-html-table.bp3-html-table-condensed td, table.bp3-html-table.bp3-small th,
table.bp3-html-table.bp3-small td{
  padding-bottom:6px;
  padding-top:6px; }

table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
  background:rgba(191, 204, 214, 0.15); }

table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
  -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered tbody tr td,
table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
  -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
  table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
    -webkit-box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
  -webkit-box-shadow:none;
          box-shadow:none; }
  table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-interactive tbody tr:hover td{
  background-color:rgba(191, 204, 214, 0.3);
  cursor:pointer; }

table.bp3-html-table.bp3-interactive tbody tr:active td{
  background-color:rgba(191, 204, 214, 0.4); }

.bp3-dark table.bp3-html-table{ }
  .bp3-dark table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
    background:rgba(92, 112, 128, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td,
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child),
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered tfoot tr td:not(:first-child){
      -webkit-box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15);
              box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
    -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
    .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:first-child{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:hover td{
    background-color:rgba(92, 112, 128, 0.3);
    cursor:pointer; }
  .bp3-dark table.bp3-html-table.bp3-interactive tbody tr:active td{
    background-color:rgba(92, 112, 128, 0.4); }

.bp3-key-combo{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center; }
  .bp3-key-combo > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-key-combo > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-key-combo::before,
  .bp3-key-combo > *{
    margin-right:5px; }
  .bp3-key-combo:empty::before,
  .bp3-key-combo > :last-child{
    margin-right:0; }

.bp3-hotkey-dialog{
  padding-bottom:0;
  top:40px; }
  .bp3-hotkey-dialog .bp3-dialog-body{
    margin:0;
    padding:0; }
  .bp3-hotkey-dialog .bp3-hotkey-label{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1; }

.bp3-hotkey-column{
  margin:auto;
  max-height:80vh;
  overflow-y:auto;
  padding:30px; }
  .bp3-hotkey-column .bp3-heading{
    margin-bottom:20px; }
    .bp3-hotkey-column .bp3-heading:not(:first-child){
      margin-top:40px; }

.bp3-hotkey{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:justify;
      -ms-flex-pack:justify;
          justify-content:space-between;
  margin-left:0;
  margin-right:0; }
  .bp3-hotkey:not(:last-child){
    margin-bottom:10px; }
.bp3-icon{
  display:inline-block;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  vertical-align:text-bottom; }
  .bp3-icon:not(:empty)::before{
    content:"" !important;
    content:unset !important; }
  .bp3-icon > svg{
    display:block; }
    .bp3-icon > svg:not([fill]){
      fill:currentColor; }

.bp3-icon.bp3-intent-primary, .bp3-icon-standard.bp3-intent-primary, .bp3-icon-large.bp3-intent-primary{
  color:#106ba3; }
  .bp3-dark .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-icon-large.bp3-intent-primary{
    color:#48aff0; }

.bp3-icon.bp3-intent-success, .bp3-icon-standard.bp3-intent-success, .bp3-icon-large.bp3-intent-success{
  color:#0d8050; }
  .bp3-dark .bp3-icon.bp3-intent-success, .bp3-dark .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-icon-large.bp3-intent-success{
    color:#3dcc91; }

.bp3-icon.bp3-intent-warning, .bp3-icon-standard.bp3-intent-warning, .bp3-icon-large.bp3-intent-warning{
  color:#bf7326; }
  .bp3-dark .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-icon-large.bp3-intent-warning{
    color:#ffb366; }

.bp3-icon.bp3-intent-danger, .bp3-icon-standard.bp3-intent-danger, .bp3-icon-large.bp3-intent-danger{
  color:#c23030; }
  .bp3-dark .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-icon-large.bp3-intent-danger{
    color:#ff7373; }

span.bp3-icon-standard{
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon-large{
  font-family:"Icons20", sans-serif;
  font-size:20px;
  font-style:normal;
  font-weight:400;
  line-height:1;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon:empty{
  font-family:"Icons20";
  font-size:inherit;
  font-style:normal;
  font-weight:400;
  line-height:1; }
  span.bp3-icon:empty::before{
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased; }

.bp3-icon-add::before{
  content:""; }

.bp3-icon-add-column-left::before{
  content:""; }

.bp3-icon-add-column-right::before{
  content:""; }

.bp3-icon-add-row-bottom::before{
  content:""; }

.bp3-icon-add-row-top::before{
  content:""; }

.bp3-icon-add-to-artifact::before{
  content:""; }

.bp3-icon-add-to-folder::before{
  content:""; }

.bp3-icon-airplane::before{
  content:""; }

.bp3-icon-align-center::before{
  content:""; }

.bp3-icon-align-justify::before{
  content:""; }

.bp3-icon-align-left::before{
  content:""; }

.bp3-icon-align-right::before{
  content:""; }

.bp3-icon-alignment-bottom::before{
  content:""; }

.bp3-icon-alignment-horizontal-center::before{
  content:""; }

.bp3-icon-alignment-left::before{
  content:""; }

.bp3-icon-alignment-right::before{
  content:""; }

.bp3-icon-alignment-top::before{
  content:""; }

.bp3-icon-alignment-vertical-center::before{
  content:""; }

.bp3-icon-annotation::before{
  content:""; }

.bp3-icon-application::before{
  content:""; }

.bp3-icon-applications::before{
  content:""; }

.bp3-icon-archive::before{
  content:""; }

.bp3-icon-arrow-bottom-left::before{
  content:"↙"; }

.bp3-icon-arrow-bottom-right::before{
  content:"↘"; }

.bp3-icon-arrow-down::before{
  content:"↓"; }

.bp3-icon-arrow-left::before{
  content:"←"; }

.bp3-icon-arrow-right::before{
  content:"→"; }

.bp3-icon-arrow-top-left::before{
  content:"↖"; }

.bp3-icon-arrow-top-right::before{
  content:"↗"; }

.bp3-icon-arrow-up::before{
  content:"↑"; }

.bp3-icon-arrows-horizontal::before{
  content:"↔"; }

.bp3-icon-arrows-vertical::before{
  content:"↕"; }

.bp3-icon-asterisk::before{
  content:"*"; }

.bp3-icon-automatic-updates::before{
  content:""; }

.bp3-icon-badge::before{
  content:""; }

.bp3-icon-ban-circle::before{
  content:""; }

.bp3-icon-bank-account::before{
  content:""; }

.bp3-icon-barcode::before{
  content:""; }

.bp3-icon-blank::before{
  content:""; }

.bp3-icon-blocked-person::before{
  content:""; }

.bp3-icon-bold::before{
  content:""; }

.bp3-icon-book::before{
  content:""; }

.bp3-icon-bookmark::before{
  content:""; }

.bp3-icon-box::before{
  content:""; }

.bp3-icon-briefcase::before{
  content:""; }

.bp3-icon-bring-data::before{
  content:""; }

.bp3-icon-build::before{
  content:""; }

.bp3-icon-calculator::before{
  content:""; }

.bp3-icon-calendar::before{
  content:""; }

.bp3-icon-camera::before{
  content:""; }

.bp3-icon-caret-down::before{
  content:"⌄"; }

.bp3-icon-caret-left::before{
  content:"〈"; }

.bp3-icon-caret-right::before{
  content:"〉"; }

.bp3-icon-caret-up::before{
  content:"⌃"; }

.bp3-icon-cell-tower::before{
  content:""; }

.bp3-icon-changes::before{
  content:""; }

.bp3-icon-chart::before{
  content:""; }

.bp3-icon-chat::before{
  content:""; }

.bp3-icon-chevron-backward::before{
  content:""; }

.bp3-icon-chevron-down::before{
  content:""; }

.bp3-icon-chevron-forward::before{
  content:""; }

.bp3-icon-chevron-left::before{
  content:""; }

.bp3-icon-chevron-right::before{
  content:""; }

.bp3-icon-chevron-up::before{
  content:""; }

.bp3-icon-circle::before{
  content:""; }

.bp3-icon-circle-arrow-down::before{
  content:""; }

.bp3-icon-circle-arrow-left::before{
  content:""; }

.bp3-icon-circle-arrow-right::before{
  content:""; }

.bp3-icon-circle-arrow-up::before{
  content:""; }

.bp3-icon-citation::before{
  content:""; }

.bp3-icon-clean::before{
  content:""; }

.bp3-icon-clipboard::before{
  content:""; }

.bp3-icon-cloud::before{
  content:"☁"; }

.bp3-icon-cloud-download::before{
  content:""; }

.bp3-icon-cloud-upload::before{
  content:""; }

.bp3-icon-code::before{
  content:""; }

.bp3-icon-code-block::before{
  content:""; }

.bp3-icon-cog::before{
  content:""; }

.bp3-icon-collapse-all::before{
  content:""; }

.bp3-icon-column-layout::before{
  content:""; }

.bp3-icon-comment::before{
  content:""; }

.bp3-icon-comparison::before{
  content:""; }

.bp3-icon-compass::before{
  content:""; }

.bp3-icon-compressed::before{
  content:""; }

.bp3-icon-confirm::before{
  content:""; }

.bp3-icon-console::before{
  content:""; }

.bp3-icon-contrast::before{
  content:""; }

.bp3-icon-control::before{
  content:""; }

.bp3-icon-credit-card::before{
  content:""; }

.bp3-icon-cross::before{
  content:"✗"; }

.bp3-icon-crown::before{
  content:""; }

.bp3-icon-cube::before{
  content:""; }

.bp3-icon-cube-add::before{
  content:""; }

.bp3-icon-cube-remove::before{
  content:""; }

.bp3-icon-curved-range-chart::before{
  content:""; }

.bp3-icon-cut::before{
  content:""; }

.bp3-icon-dashboard::before{
  content:""; }

.bp3-icon-data-lineage::before{
  content:""; }

.bp3-icon-database::before{
  content:""; }

.bp3-icon-delete::before{
  content:""; }

.bp3-icon-delta::before{
  content:"Δ"; }

.bp3-icon-derive-column::before{
  content:""; }

.bp3-icon-desktop::before{
  content:""; }

.bp3-icon-diagnosis::before{
  content:""; }

.bp3-icon-diagram-tree::before{
  content:""; }

.bp3-icon-direction-left::before{
  content:""; }

.bp3-icon-direction-right::before{
  content:""; }

.bp3-icon-disable::before{
  content:""; }

.bp3-icon-document::before{
  content:""; }

.bp3-icon-document-open::before{
  content:""; }

.bp3-icon-document-share::before{
  content:""; }

.bp3-icon-dollar::before{
  content:"$"; }

.bp3-icon-dot::before{
  content:"•"; }

.bp3-icon-double-caret-horizontal::before{
  content:""; }

.bp3-icon-double-caret-vertical::before{
  content:""; }

.bp3-icon-double-chevron-down::before{
  content:""; }

.bp3-icon-double-chevron-left::before{
  content:""; }

.bp3-icon-double-chevron-right::before{
  content:""; }

.bp3-icon-double-chevron-up::before{
  content:""; }

.bp3-icon-doughnut-chart::before{
  content:""; }

.bp3-icon-download::before{
  content:""; }

.bp3-icon-drag-handle-horizontal::before{
  content:""; }

.bp3-icon-drag-handle-vertical::before{
  content:""; }

.bp3-icon-draw::before{
  content:""; }

.bp3-icon-drive-time::before{
  content:""; }

.bp3-icon-duplicate::before{
  content:""; }

.bp3-icon-edit::before{
  content:"✎"; }

.bp3-icon-eject::before{
  content:"⏏"; }

.bp3-icon-endorsed::before{
  content:""; }

.bp3-icon-envelope::before{
  content:"✉"; }

.bp3-icon-equals::before{
  content:""; }

.bp3-icon-eraser::before{
  content:""; }

.bp3-icon-error::before{
  content:""; }

.bp3-icon-euro::before{
  content:"€"; }

.bp3-icon-exchange::before{
  content:""; }

.bp3-icon-exclude-row::before{
  content:""; }

.bp3-icon-expand-all::before{
  content:""; }

.bp3-icon-export::before{
  content:""; }

.bp3-icon-eye-off::before{
  content:""; }

.bp3-icon-eye-on::before{
  content:""; }

.bp3-icon-eye-open::before{
  content:""; }

.bp3-icon-fast-backward::before{
  content:""; }

.bp3-icon-fast-forward::before{
  content:""; }

.bp3-icon-feed::before{
  content:""; }

.bp3-icon-feed-subscribed::before{
  content:""; }

.bp3-icon-film::before{
  content:""; }

.bp3-icon-filter::before{
  content:""; }

.bp3-icon-filter-keep::before{
  content:""; }

.bp3-icon-filter-list::before{
  content:""; }

.bp3-icon-filter-open::before{
  content:""; }

.bp3-icon-filter-remove::before{
  content:""; }

.bp3-icon-flag::before{
  content:"⚑"; }

.bp3-icon-flame::before{
  content:""; }

.bp3-icon-flash::before{
  content:""; }

.bp3-icon-floppy-disk::before{
  content:""; }

.bp3-icon-flow-branch::before{
  content:""; }

.bp3-icon-flow-end::before{
  content:""; }

.bp3-icon-flow-linear::before{
  content:""; }

.bp3-icon-flow-review::before{
  content:""; }

.bp3-icon-flow-review-branch::before{
  content:""; }

.bp3-icon-flows::before{
  content:""; }

.bp3-icon-folder-close::before{
  content:""; }

.bp3-icon-folder-new::before{
  content:""; }

.bp3-icon-folder-open::before{
  content:""; }

.bp3-icon-folder-shared::before{
  content:""; }

.bp3-icon-folder-shared-open::before{
  content:""; }

.bp3-icon-follower::before{
  content:""; }

.bp3-icon-following::before{
  content:""; }

.bp3-icon-font::before{
  content:""; }

.bp3-icon-fork::before{
  content:""; }

.bp3-icon-form::before{
  content:""; }

.bp3-icon-full-circle::before{
  content:""; }

.bp3-icon-full-stacked-chart::before{
  content:""; }

.bp3-icon-fullscreen::before{
  content:""; }

.bp3-icon-function::before{
  content:""; }

.bp3-icon-gantt-chart::before{
  content:""; }

.bp3-icon-geolocation::before{
  content:""; }

.bp3-icon-geosearch::before{
  content:""; }

.bp3-icon-git-branch::before{
  content:""; }

.bp3-icon-git-commit::before{
  content:""; }

.bp3-icon-git-merge::before{
  content:""; }

.bp3-icon-git-new-branch::before{
  content:""; }

.bp3-icon-git-pull::before{
  content:""; }

.bp3-icon-git-push::before{
  content:""; }

.bp3-icon-git-repo::before{
  content:""; }

.bp3-icon-glass::before{
  content:""; }

.bp3-icon-globe::before{
  content:""; }

.bp3-icon-globe-network::before{
  content:""; }

.bp3-icon-graph::before{
  content:""; }

.bp3-icon-graph-remove::before{
  content:""; }

.bp3-icon-greater-than::before{
  content:""; }

.bp3-icon-greater-than-or-equal-to::before{
  content:""; }

.bp3-icon-grid::before{
  content:""; }

.bp3-icon-grid-view::before{
  content:""; }

.bp3-icon-group-objects::before{
  content:""; }

.bp3-icon-grouped-bar-chart::before{
  content:""; }

.bp3-icon-hand::before{
  content:""; }

.bp3-icon-hand-down::before{
  content:""; }

.bp3-icon-hand-left::before{
  content:""; }

.bp3-icon-hand-right::before{
  content:""; }

.bp3-icon-hand-up::before{
  content:""; }

.bp3-icon-header::before{
  content:""; }

.bp3-icon-header-one::before{
  content:""; }

.bp3-icon-header-two::before{
  content:""; }

.bp3-icon-headset::before{
  content:""; }

.bp3-icon-heart::before{
  content:"♥"; }

.bp3-icon-heart-broken::before{
  content:""; }

.bp3-icon-heat-grid::before{
  content:""; }

.bp3-icon-heatmap::before{
  content:""; }

.bp3-icon-help::before{
  content:"?"; }

.bp3-icon-helper-management::before{
  content:""; }

.bp3-icon-highlight::before{
  content:""; }

.bp3-icon-history::before{
  content:""; }

.bp3-icon-home::before{
  content:"⌂"; }

.bp3-icon-horizontal-bar-chart::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-asc::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-desc::before{
  content:""; }

.bp3-icon-horizontal-distribution::before{
  content:""; }

.bp3-icon-id-number::before{
  content:""; }

.bp3-icon-image-rotate-left::before{
  content:""; }

.bp3-icon-image-rotate-right::before{
  content:""; }

.bp3-icon-import::before{
  content:""; }

.bp3-icon-inbox::before{
  content:""; }

.bp3-icon-inbox-filtered::before{
  content:""; }

.bp3-icon-inbox-geo::before{
  content:""; }

.bp3-icon-inbox-search::before{
  content:""; }

.bp3-icon-inbox-update::before{
  content:""; }

.bp3-icon-info-sign::before{
  content:"ℹ"; }

.bp3-icon-inheritance::before{
  content:""; }

.bp3-icon-inner-join::before{
  content:""; }

.bp3-icon-insert::before{
  content:""; }

.bp3-icon-intersection::before{
  content:""; }

.bp3-icon-ip-address::before{
  content:""; }

.bp3-icon-issue::before{
  content:""; }

.bp3-icon-issue-closed::before{
  content:""; }

.bp3-icon-issue-new::before{
  content:""; }

.bp3-icon-italic::before{
  content:""; }

.bp3-icon-join-table::before{
  content:""; }

.bp3-icon-key::before{
  content:""; }

.bp3-icon-key-backspace::before{
  content:""; }

.bp3-icon-key-command::before{
  content:""; }

.bp3-icon-key-control::before{
  content:""; }

.bp3-icon-key-delete::before{
  content:""; }

.bp3-icon-key-enter::before{
  content:""; }

.bp3-icon-key-escape::before{
  content:""; }

.bp3-icon-key-option::before{
  content:""; }

.bp3-icon-key-shift::before{
  content:""; }

.bp3-icon-key-tab::before{
  content:""; }

.bp3-icon-known-vehicle::before{
  content:""; }

.bp3-icon-lab-test::before{
  content:""; }

.bp3-icon-label::before{
  content:""; }

.bp3-icon-layer::before{
  content:""; }

.bp3-icon-layers::before{
  content:""; }

.bp3-icon-layout::before{
  content:""; }

.bp3-icon-layout-auto::before{
  content:""; }

.bp3-icon-layout-balloon::before{
  content:""; }

.bp3-icon-layout-circle::before{
  content:""; }

.bp3-icon-layout-grid::before{
  content:""; }

.bp3-icon-layout-group-by::before{
  content:""; }

.bp3-icon-layout-hierarchy::before{
  content:""; }

.bp3-icon-layout-linear::before{
  content:""; }

.bp3-icon-layout-skew-grid::before{
  content:""; }

.bp3-icon-layout-sorted-clusters::before{
  content:""; }

.bp3-icon-learning::before{
  content:""; }

.bp3-icon-left-join::before{
  content:""; }

.bp3-icon-less-than::before{
  content:""; }

.bp3-icon-less-than-or-equal-to::before{
  content:""; }

.bp3-icon-lifesaver::before{
  content:""; }

.bp3-icon-lightbulb::before{
  content:""; }

.bp3-icon-link::before{
  content:""; }

.bp3-icon-list::before{
  content:"☰"; }

.bp3-icon-list-columns::before{
  content:""; }

.bp3-icon-list-detail-view::before{
  content:""; }

.bp3-icon-locate::before{
  content:""; }

.bp3-icon-lock::before{
  content:""; }

.bp3-icon-log-in::before{
  content:""; }

.bp3-icon-log-out::before{
  content:""; }

.bp3-icon-manual::before{
  content:""; }

.bp3-icon-manually-entered-data::before{
  content:""; }

.bp3-icon-map::before{
  content:""; }

.bp3-icon-map-create::before{
  content:""; }

.bp3-icon-map-marker::before{
  content:""; }

.bp3-icon-maximize::before{
  content:""; }

.bp3-icon-media::before{
  content:""; }

.bp3-icon-menu::before{
  content:""; }

.bp3-icon-menu-closed::before{
  content:""; }

.bp3-icon-menu-open::before{
  content:""; }

.bp3-icon-merge-columns::before{
  content:""; }

.bp3-icon-merge-links::before{
  content:""; }

.bp3-icon-minimize::before{
  content:""; }

.bp3-icon-minus::before{
  content:"−"; }

.bp3-icon-mobile-phone::before{
  content:""; }

.bp3-icon-mobile-video::before{
  content:""; }

.bp3-icon-moon::before{
  content:""; }

.bp3-icon-more::before{
  content:""; }

.bp3-icon-mountain::before{
  content:""; }

.bp3-icon-move::before{
  content:""; }

.bp3-icon-mugshot::before{
  content:""; }

.bp3-icon-multi-select::before{
  content:""; }

.bp3-icon-music::before{
  content:""; }

.bp3-icon-new-drawing::before{
  content:""; }

.bp3-icon-new-grid-item::before{
  content:""; }

.bp3-icon-new-layer::before{
  content:""; }

.bp3-icon-new-layers::before{
  content:""; }

.bp3-icon-new-link::before{
  content:""; }

.bp3-icon-new-object::before{
  content:""; }

.bp3-icon-new-person::before{
  content:""; }

.bp3-icon-new-prescription::before{
  content:""; }

.bp3-icon-new-text-box::before{
  content:""; }

.bp3-icon-ninja::before{
  content:""; }

.bp3-icon-not-equal-to::before{
  content:""; }

.bp3-icon-notifications::before{
  content:""; }

.bp3-icon-notifications-updated::before{
  content:""; }

.bp3-icon-numbered-list::before{
  content:""; }

.bp3-icon-numerical::before{
  content:""; }

.bp3-icon-office::before{
  content:""; }

.bp3-icon-offline::before{
  content:""; }

.bp3-icon-oil-field::before{
  content:""; }

.bp3-icon-one-column::before{
  content:""; }

.bp3-icon-outdated::before{
  content:""; }

.bp3-icon-page-layout::before{
  content:""; }

.bp3-icon-panel-stats::before{
  content:""; }

.bp3-icon-panel-table::before{
  content:""; }

.bp3-icon-paperclip::before{
  content:""; }

.bp3-icon-paragraph::before{
  content:""; }

.bp3-icon-path::before{
  content:""; }

.bp3-icon-path-search::before{
  content:""; }

.bp3-icon-pause::before{
  content:""; }

.bp3-icon-people::before{
  content:""; }

.bp3-icon-percentage::before{
  content:""; }

.bp3-icon-person::before{
  content:""; }

.bp3-icon-phone::before{
  content:"☎"; }

.bp3-icon-pie-chart::before{
  content:""; }

.bp3-icon-pin::before{
  content:""; }

.bp3-icon-pivot::before{
  content:""; }

.bp3-icon-pivot-table::before{
  content:""; }

.bp3-icon-play::before{
  content:""; }

.bp3-icon-plus::before{
  content:"+"; }

.bp3-icon-polygon-filter::before{
  content:""; }

.bp3-icon-power::before{
  content:""; }

.bp3-icon-predictive-analysis::before{
  content:""; }

.bp3-icon-prescription::before{
  content:""; }

.bp3-icon-presentation::before{
  content:""; }

.bp3-icon-print::before{
  content:"⎙"; }

.bp3-icon-projects::before{
  content:""; }

.bp3-icon-properties::before{
  content:""; }

.bp3-icon-property::before{
  content:""; }

.bp3-icon-publish-function::before{
  content:""; }

.bp3-icon-pulse::before{
  content:""; }

.bp3-icon-random::before{
  content:""; }

.bp3-icon-record::before{
  content:""; }

.bp3-icon-redo::before{
  content:""; }

.bp3-icon-refresh::before{
  content:""; }

.bp3-icon-regression-chart::before{
  content:""; }

.bp3-icon-remove::before{
  content:""; }

.bp3-icon-remove-column::before{
  content:""; }

.bp3-icon-remove-column-left::before{
  content:""; }

.bp3-icon-remove-column-right::before{
  content:""; }

.bp3-icon-remove-row-bottom::before{
  content:""; }

.bp3-icon-remove-row-top::before{
  content:""; }

.bp3-icon-repeat::before{
  content:""; }

.bp3-icon-reset::before{
  content:""; }

.bp3-icon-resolve::before{
  content:""; }

.bp3-icon-rig::before{
  content:""; }

.bp3-icon-right-join::before{
  content:""; }

.bp3-icon-ring::before{
  content:""; }

.bp3-icon-rotate-document::before{
  content:""; }

.bp3-icon-rotate-page::before{
  content:""; }

.bp3-icon-satellite::before{
  content:""; }

.bp3-icon-saved::before{
  content:""; }

.bp3-icon-scatter-plot::before{
  content:""; }

.bp3-icon-search::before{
  content:""; }

.bp3-icon-search-around::before{
  content:""; }

.bp3-icon-search-template::before{
  content:""; }

.bp3-icon-search-text::before{
  content:""; }

.bp3-icon-segmented-control::before{
  content:""; }

.bp3-icon-select::before{
  content:""; }

.bp3-icon-selection::before{
  content:"⦿"; }

.bp3-icon-send-to::before{
  content:""; }

.bp3-icon-send-to-graph::before{
  content:""; }

.bp3-icon-send-to-map::before{
  content:""; }

.bp3-icon-series-add::before{
  content:""; }

.bp3-icon-series-configuration::before{
  content:""; }

.bp3-icon-series-derived::before{
  content:""; }

.bp3-icon-series-filtered::before{
  content:""; }

.bp3-icon-series-search::before{
  content:""; }

.bp3-icon-settings::before{
  content:""; }

.bp3-icon-share::before{
  content:""; }

.bp3-icon-shield::before{
  content:""; }

.bp3-icon-shop::before{
  content:""; }

.bp3-icon-shopping-cart::before{
  content:""; }

.bp3-icon-signal-search::before{
  content:""; }

.bp3-icon-sim-card::before{
  content:""; }

.bp3-icon-slash::before{
  content:""; }

.bp3-icon-small-cross::before{
  content:""; }

.bp3-icon-small-minus::before{
  content:""; }

.bp3-icon-small-plus::before{
  content:""; }

.bp3-icon-small-tick::before{
  content:""; }

.bp3-icon-snowflake::before{
  content:""; }

.bp3-icon-social-media::before{
  content:""; }

.bp3-icon-sort::before{
  content:""; }

.bp3-icon-sort-alphabetical::before{
  content:""; }

.bp3-icon-sort-alphabetical-desc::before{
  content:""; }

.bp3-icon-sort-asc::before{
  content:""; }

.bp3-icon-sort-desc::before{
  content:""; }

.bp3-icon-sort-numerical::before{
  content:""; }

.bp3-icon-sort-numerical-desc::before{
  content:""; }

.bp3-icon-split-columns::before{
  content:""; }

.bp3-icon-square::before{
  content:""; }

.bp3-icon-stacked-chart::before{
  content:""; }

.bp3-icon-star::before{
  content:"★"; }

.bp3-icon-star-empty::before{
  content:"☆"; }

.bp3-icon-step-backward::before{
  content:""; }

.bp3-icon-step-chart::before{
  content:""; }

.bp3-icon-step-forward::before{
  content:""; }

.bp3-icon-stop::before{
  content:""; }

.bp3-icon-stopwatch::before{
  content:""; }

.bp3-icon-strikethrough::before{
  content:""; }

.bp3-icon-style::before{
  content:""; }

.bp3-icon-swap-horizontal::before{
  content:""; }

.bp3-icon-swap-vertical::before{
  content:""; }

.bp3-icon-symbol-circle::before{
  content:""; }

.bp3-icon-symbol-cross::before{
  content:""; }

.bp3-icon-symbol-diamond::before{
  content:""; }

.bp3-icon-symbol-square::before{
  content:""; }

.bp3-icon-symbol-triangle-down::before{
  content:""; }

.bp3-icon-symbol-triangle-up::before{
  content:""; }

.bp3-icon-tag::before{
  content:""; }

.bp3-icon-take-action::before{
  content:""; }

.bp3-icon-taxi::before{
  content:""; }

.bp3-icon-text-highlight::before{
  content:""; }

.bp3-icon-th::before{
  content:""; }

.bp3-icon-th-derived::before{
  content:""; }

.bp3-icon-th-disconnect::before{
  content:""; }

.bp3-icon-th-filtered::before{
  content:""; }

.bp3-icon-th-list::before{
  content:""; }

.bp3-icon-thumbs-down::before{
  content:""; }

.bp3-icon-thumbs-up::before{
  content:""; }

.bp3-icon-tick::before{
  content:"✓"; }

.bp3-icon-tick-circle::before{
  content:""; }

.bp3-icon-time::before{
  content:"⏲"; }

.bp3-icon-timeline-area-chart::before{
  content:""; }

.bp3-icon-timeline-bar-chart::before{
  content:""; }

.bp3-icon-timeline-events::before{
  content:""; }

.bp3-icon-timeline-line-chart::before{
  content:""; }

.bp3-icon-tint::before{
  content:""; }

.bp3-icon-torch::before{
  content:""; }

.bp3-icon-tractor::before{
  content:""; }

.bp3-icon-train::before{
  content:""; }

.bp3-icon-translate::before{
  content:""; }

.bp3-icon-trash::before{
  content:""; }

.bp3-icon-tree::before{
  content:""; }

.bp3-icon-trending-down::before{
  content:""; }

.bp3-icon-trending-up::before{
  content:""; }

.bp3-icon-truck::before{
  content:""; }

.bp3-icon-two-columns::before{
  content:""; }

.bp3-icon-unarchive::before{
  content:""; }

.bp3-icon-underline::before{
  content:"⎁"; }

.bp3-icon-undo::before{
  content:"⎌"; }

.bp3-icon-ungroup-objects::before{
  content:""; }

.bp3-icon-unknown-vehicle::before{
  content:""; }

.bp3-icon-unlock::before{
  content:""; }

.bp3-icon-unpin::before{
  content:""; }

.bp3-icon-unresolve::before{
  content:""; }

.bp3-icon-updated::before{
  content:""; }

.bp3-icon-upload::before{
  content:""; }

.bp3-icon-user::before{
  content:""; }

.bp3-icon-variable::before{
  content:""; }

.bp3-icon-vertical-bar-chart-asc::before{
  content:""; }

.bp3-icon-vertical-bar-chart-desc::before{
  content:""; }

.bp3-icon-vertical-distribution::before{
  content:""; }

.bp3-icon-video::before{
  content:""; }

.bp3-icon-volume-down::before{
  content:""; }

.bp3-icon-volume-off::before{
  content:""; }

.bp3-icon-volume-up::before{
  content:""; }

.bp3-icon-walk::before{
  content:""; }

.bp3-icon-warning-sign::before{
  content:""; }

.bp3-icon-waterfall-chart::before{
  content:""; }

.bp3-icon-widget::before{
  content:""; }

.bp3-icon-widget-button::before{
  content:""; }

.bp3-icon-widget-footer::before{
  content:""; }

.bp3-icon-widget-header::before{
  content:""; }

.bp3-icon-wrench::before{
  content:""; }

.bp3-icon-zoom-in::before{
  content:""; }

.bp3-icon-zoom-out::before{
  content:""; }

.bp3-icon-zoom-to-fit::before{
  content:""; }
.bp3-submenu > .bp3-popover-wrapper{
  display:block; }

.bp3-submenu .bp3-popover-target{
  display:block; }
  .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{ }

.bp3-submenu.bp3-popover{
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0 5px; }
  .bp3-submenu.bp3-popover > .bp3-popover-content{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-submenu.bp3-popover, .bp3-submenu.bp3-popover.bp3-dark{
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-dark .bp3-submenu.bp3-popover > .bp3-popover-content, .bp3-submenu.bp3-popover.bp3-dark > .bp3-popover-content{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
.bp3-menu{
  background:#ffffff;
  border-radius:3px;
  color:#182026;
  list-style:none;
  margin:0;
  min-width:180px;
  padding:5px;
  text-align:left; }

.bp3-menu-divider{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px; }
  .bp3-dark .bp3-menu-divider{
    border-top-color:rgba(255, 255, 255, 0.15); }

.bp3-menu-item{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  border-radius:2px;
  color:inherit;
  line-height:20px;
  padding:5px 7px;
  text-decoration:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-menu-item > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-menu-item > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-menu-item::before,
  .bp3-menu-item > *{
    margin-right:7px; }
  .bp3-menu-item:empty::before,
  .bp3-menu-item > :last-child{
    margin-right:0; }
  .bp3-menu-item > .bp3-fill{
    word-break:break-word; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    background-color:rgba(167, 182, 194, 0.3);
    cursor:pointer;
    text-decoration:none; }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-dark .bp3-menu-item{
    color:inherit; }
    .bp3-dark .bp3-menu-item:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      background-color:rgba(138, 155, 168, 0.15);
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-disabled{
      background-color:inherit;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-menu-item.bp3-intent-primary{
    color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-primary::before, .bp3-menu-item.bp3-intent-primary::after,
    .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary:active, .bp3-menu-item.bp3-intent-primary:active::before, .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-success{
    color:#0d8050; }
    .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-success::before, .bp3-menu-item.bp3-intent-success::after,
    .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-menu-item.bp3-intent-success:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success:active, .bp3-menu-item.bp3-intent-success:active::before, .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-warning{
    color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-warning::before, .bp3-menu-item.bp3-intent-warning::after,
    .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning:active, .bp3-menu-item.bp3-intent-warning:active::before, .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-danger{
    color:#c23030; }
    .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-danger::before, .bp3-menu-item.bp3-intent-danger::after,
    .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger:active, .bp3-menu-item.bp3-intent-danger:active::before, .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    margin-right:7px; }
  .bp3-menu-item::before,
  .bp3-menu-item > .bp3-icon{
    color:#5c7080;
    margin-top:2px; }
  .bp3-menu-item .bp3-menu-item-label{
    color:#5c7080; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    color:inherit; }
  .bp3-menu-item.bp3-active, .bp3-menu-item:active{
    background-color:rgba(115, 134, 148, 0.3); }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit !important;
    color:rgba(92, 112, 128, 0.6) !important;
    cursor:not-allowed !important;
    outline:none !important; }
    .bp3-menu-item.bp3-disabled::before,
    .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-large .bp3-menu-item{
    font-size:16px;
    line-height:22px;
    padding:9px 7px; }
    .bp3-large .bp3-menu-item .bp3-icon{
      margin-top:3px; }
    .bp3-large .bp3-menu-item::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      margin-right:10px;
      margin-top:1px; }

button.bp3-menu-item{
  background:none;
  border:none;
  text-align:left;
  width:100%; }
.bp3-menu-header{
  border-top:1px solid rgba(16, 22, 26, 0.15);
  display:block;
  margin:5px;
  cursor:default;
  padding-left:2px; }
  .bp3-dark .bp3-menu-header{
    border-top-color:rgba(255, 255, 255, 0.15); }
  .bp3-menu-header:first-of-type{
    border-top:none; }
  .bp3-menu-header > h6{
    color:#182026;
    font-weight:600;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    line-height:17px;
    margin:0;
    padding:10px 7px 0 1px; }
    .bp3-dark .bp3-menu-header > h6{
      color:#f5f8fa; }
  .bp3-menu-header:first-of-type > h6{
    padding-top:0; }
  .bp3-large .bp3-menu-header > h6{
    font-size:18px;
    padding-bottom:5px;
    padding-top:15px; }
  .bp3-large .bp3-menu-header:first-of-type > h6{
    padding-top:0; }

.bp3-dark .bp3-menu{
  background:#30404d;
  color:#f5f8fa; }

.bp3-dark .bp3-menu-item{ }
  .bp3-dark .bp3-menu-item.bp3-intent-primary{
    color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary::before, .bp3-dark .bp3-menu-item.bp3-intent-primary::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#48aff0; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary:active, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-success{
    color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-success::before, .bp3-dark .bp3-menu-item.bp3-intent-success::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#3dcc91; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success:active, .bp3-dark .bp3-menu-item.bp3-intent-success:active::before, .bp3-dark .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning{
    color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning::before, .bp3-dark .bp3-menu-item.bp3-intent-warning::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#ffb366; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning:active, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger{
    color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger::before, .bp3-dark .bp3-menu-item.bp3-intent-danger::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#ff7373; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label,
    .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger:active, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-dark .bp3-menu-item::before,
  .bp3-dark .bp3-menu-item > .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item .bp3-menu-item-label{
    color:#a7b6c2; }
  .bp3-dark .bp3-menu-item.bp3-active, .bp3-dark .bp3-menu-item:active{
    background-color:rgba(138, 155, 168, 0.3); }
  .bp3-dark .bp3-menu-item.bp3-disabled{
    color:rgba(167, 182, 194, 0.6) !important; }
    .bp3-dark .bp3-menu-item.bp3-disabled::before,
    .bp3-dark .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-dark .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(167, 182, 194, 0.6) !important; }

.bp3-dark .bp3-menu-divider,
.bp3-dark .bp3-menu-header{
  border-color:rgba(255, 255, 255, 0.15); }

.bp3-dark .bp3-menu-header > h6{
  color:#f5f8fa; }

.bp3-label .bp3-menu{
  margin-top:5px; }
.bp3-navbar{
  background-color:#ffffff;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  height:50px;
  padding:0 15px;
  position:relative;
  width:100%;
  z-index:10; }
  .bp3-navbar.bp3-dark,
  .bp3-dark .bp3-navbar{
    background-color:#394b59; }
  .bp3-navbar.bp3-dark{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-navbar{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-navbar.bp3-fixed-top{
    left:0;
    position:fixed;
    right:0;
    top:0; }

.bp3-navbar-heading{
  font-size:16px;
  margin-right:15px; }

.bp3-navbar-group{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:50px; }
  .bp3-navbar-group.bp3-align-left{
    float:left; }
  .bp3-navbar-group.bp3-align-right{
    float:right; }

.bp3-navbar-divider{
  border-left:1px solid rgba(16, 22, 26, 0.15);
  height:20px;
  margin:0 10px; }
  .bp3-dark .bp3-navbar-divider{
    border-left-color:rgba(255, 255, 255, 0.15); }
.bp3-non-ideal-state{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  height:100%;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  text-align:center;
  width:100%; }
  .bp3-non-ideal-state > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-non-ideal-state > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-non-ideal-state::before,
  .bp3-non-ideal-state > *{
    margin-bottom:20px; }
  .bp3-non-ideal-state:empty::before,
  .bp3-non-ideal-state > :last-child{
    margin-bottom:0; }
  .bp3-non-ideal-state > *{
    max-width:400px; }

.bp3-non-ideal-state-visual{
  color:rgba(92, 112, 128, 0.6);
  font-size:60px; }
  .bp3-dark .bp3-non-ideal-state-visual{
    color:rgba(167, 182, 194, 0.6); }

.bp3-overflow-list{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:nowrap;
      flex-wrap:nowrap;
  min-width:0; }

.bp3-overflow-list-spacer{
  -ms-flex-negative:1;
      flex-shrink:1;
  width:1px; }

body.bp3-overlay-open{
  overflow:hidden; }

.bp3-overlay{
  bottom:0;
  left:0;
  position:static;
  right:0;
  top:0;
  z-index:20; }
  .bp3-overlay:not(.bp3-overlay-open){
    pointer-events:none; }
  .bp3-overlay.bp3-overlay-container{
    overflow:hidden;
    position:fixed; }
    .bp3-overlay.bp3-overlay-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-scroll-container{
    overflow:auto;
    position:fixed; }
    .bp3-overlay.bp3-overlay-scroll-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-inline{
    display:inline;
    overflow:visible; }

.bp3-overlay-content{
  position:fixed;
  z-index:20; }
  .bp3-overlay-inline .bp3-overlay-content,
  .bp3-overlay-scroll-container .bp3-overlay-content{
    position:absolute; }

.bp3-overlay-backdrop{
  bottom:0;
  left:0;
  position:fixed;
  right:0;
  top:0;
  opacity:1;
  background-color:rgba(16, 22, 26, 0.7);
  overflow:auto;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none;
  z-index:20; }
  .bp3-overlay-backdrop.bp3-overlay-enter, .bp3-overlay-backdrop.bp3-overlay-appear{
    opacity:0; }
  .bp3-overlay-backdrop.bp3-overlay-enter-active, .bp3-overlay-backdrop.bp3-overlay-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop.bp3-overlay-exit{
    opacity:1; }
  .bp3-overlay-backdrop.bp3-overlay-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-overlay-backdrop:focus{
    outline:none; }
  .bp3-overlay-inline .bp3-overlay-backdrop{
    position:absolute; }
.bp3-panel-stack{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack-view{
    background-color:#30404d; }
  .bp3-panel-stack-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack-push .bp3-panel-stack-enter, .bp3-panel-stack-push .bp3-panel-stack-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack-push .bp3-panel-stack-enter-active, .bp3-panel-stack-push .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-push .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-push .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-enter, .bp3-panel-stack-pop .bp3-panel-stack-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack-pop .bp3-panel-stack-enter-active, .bp3-panel-stack-pop .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack-pop .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-pop .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-panel-stack2{
  overflow:hidden;
  position:relative; }

.bp3-panel-stack2-header{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  height:30px;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack2-header > span{
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1; }
  .bp3-panel-stack2-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack2-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack2-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack2-view{
  bottom:0;
  left:0;
  position:absolute;
  right:0;
  top:0;
  background-color:#ffffff;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  overflow-y:auto;
  z-index:1; }
  .bp3-dark .bp3-panel-stack2-view{
    background-color:#30404d; }
  .bp3-panel-stack2-view:nth-last-child(n + 4){
    display:none; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter, .bp3-panel-stack2-push .bp3-panel-stack2-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack2-push .bp3-panel-stack2-enter-active, .bp3-panel-stack2-push .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-push .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter, .bp3-panel-stack2-pop .bp3-panel-stack2-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack2-pop .bp3-panel-stack2-enter-active, .bp3-panel-stack2-pop .bp3-panel-stack2-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack2-pop .bp3-panel-stack2-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-delay:0;
          transition-delay:0;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease; }
.bp3-popover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1);
  border-radius:3px;
  display:inline-block;
  z-index:20; }
  .bp3-popover .bp3-popover-arrow{
    height:30px;
    position:absolute;
    width:30px; }
    .bp3-popover .bp3-popover-arrow::before{
      height:20px;
      margin:5px;
      width:20px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover{
    margin-bottom:17px;
    margin-top:-17px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
      bottom:-11px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover{
    margin-left:17px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
      left:-11px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover{
    margin-top:17px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
      top:-11px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover{
    margin-left:-17px;
    margin-right:17px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
      right:-11px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-popover > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-popover > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
    top:-0.3934px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
    right:-0.3934px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
    left:-0.3934px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
    bottom:-0.3934px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-popover .bp3-popover-content{
    background:#ffffff;
    color:inherit; }
  .bp3-popover .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-popover .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-popover .bp3-popover-arrow-fill{
    fill:#ffffff; }
  .bp3-popover-enter > .bp3-popover, .bp3-popover-appear > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3); }
  .bp3-popover-enter-active > .bp3-popover, .bp3-popover-appear-active > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover-exit > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-popover .bp3-popover-content{
    border-radius:3px;
    position:relative; }
  .bp3-popover.bp3-popover-content-sizing .bp3-popover-content{
    max-width:350px;
    padding:20px; }
  .bp3-popover-target + .bp3-overlay .bp3-popover.bp3-popover-content-sizing{
    width:350px; }
  .bp3-popover.bp3-minimal{
    margin:0 !important; }
    .bp3-popover.bp3-minimal .bp3-popover-arrow{
      display:none; }
    .bp3-popover.bp3-minimal.bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1); }
      .bp3-popover-enter > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-enter-active > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
      .bp3-popover-exit > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-exit-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-delay:0;
                transition-delay:0;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover.bp3-dark,
  .bp3-dark .bp3-popover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-popover .bp3-popover-content{
      background:#30404d;
      color:inherit; }
    .bp3-popover.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-popover .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-popover .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-popover.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-popover .bp3-popover-arrow-fill{
      fill:#30404d; }

.bp3-popover-arrow::before{
  border-radius:2px;
  content:"";
  display:block;
  position:absolute;
  -webkit-transform:rotate(45deg);
          transform:rotate(45deg); }

.bp3-tether-pinned .bp3-popover-arrow{
  display:none; }

.bp3-popover-backdrop{
  background:rgba(255, 255, 255, 0); }

.bp3-transition-container{
  opacity:1;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  z-index:20; }
  .bp3-transition-container.bp3-popover-enter, .bp3-transition-container.bp3-popover-appear{
    opacity:0; }
  .bp3-transition-container.bp3-popover-enter-active, .bp3-transition-container.bp3-popover-appear-active{
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container.bp3-popover-exit{
    opacity:1; }
  .bp3-transition-container.bp3-popover-exit-active{
    opacity:0;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-transition-container:focus{
    outline:none; }
  .bp3-transition-container.bp3-popover-leave .bp3-popover-content{
    pointer-events:none; }
  .bp3-transition-container[data-x-out-of-boundaries]{
    display:none; }

span.bp3-popover-target{
  display:inline-block; }

.bp3-popover-wrapper.bp3-fill{
  width:100%; }

.bp3-portal{
  left:0;
  position:absolute;
  right:0;
  top:0; }
@-webkit-keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }
@keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }

.bp3-progress-bar{
  background:rgba(92, 112, 128, 0.2);
  border-radius:40px;
  display:block;
  height:8px;
  overflow:hidden;
  position:relative;
  width:100%; }
  .bp3-progress-bar .bp3-progress-meter{
    background:linear-gradient(-45deg, rgba(255, 255, 255, 0.2) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.2) 50%, rgba(255, 255, 255, 0.2) 75%, transparent 75%);
    background-color:rgba(92, 112, 128, 0.8);
    background-size:30px 30px;
    border-radius:40px;
    height:100%;
    position:absolute;
    -webkit-transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    width:100%; }
  .bp3-progress-bar:not(.bp3-no-animation):not(.bp3-no-stripes) .bp3-progress-meter{
    animation:linear-progress-bar-stripes 300ms linear infinite reverse; }
  .bp3-progress-bar.bp3-no-stripes .bp3-progress-meter{
    background-image:none; }

.bp3-dark .bp3-progress-bar{
  background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-progress-bar .bp3-progress-meter{
    background-color:#8a9ba8; }

.bp3-progress-bar.bp3-intent-primary .bp3-progress-meter{
  background-color:#137cbd; }

.bp3-progress-bar.bp3-intent-success .bp3-progress-meter{
  background-color:#0f9960; }

.bp3-progress-bar.bp3-intent-warning .bp3-progress-meter{
  background-color:#d9822b; }

.bp3-progress-bar.bp3-intent-danger .bp3-progress-meter{
  background-color:#db3737; }
@-webkit-keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
@keyframes skeleton-glow{
  from{
    background:rgba(206, 217, 224, 0.2);
    border-color:rgba(206, 217, 224, 0.2); }
  to{
    background:rgba(92, 112, 128, 0.2);
    border-color:rgba(92, 112, 128, 0.2); } }
.bp3-skeleton{
  -webkit-animation:1000ms linear infinite alternate skeleton-glow;
          animation:1000ms linear infinite alternate skeleton-glow;
  background:rgba(206, 217, 224, 0.2);
  background-clip:padding-box !important;
  border-color:rgba(206, 217, 224, 0.2) !important;
  border-radius:2px;
  -webkit-box-shadow:none !important;
          box-shadow:none !important;
  color:transparent !important;
  cursor:default;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-skeleton::before, .bp3-skeleton::after,
  .bp3-skeleton *{
    visibility:hidden !important; }
.bp3-slider{
  height:40px;
  min-width:150px;
  width:100%;
  cursor:default;
  outline:none;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-slider:hover{
    cursor:pointer; }
  .bp3-slider:active{
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-slider.bp3-disabled{
    cursor:not-allowed;
    opacity:0.5; }
  .bp3-slider.bp3-slider-unlabeled{
    height:16px; }

.bp3-slider-track,
.bp3-slider-progress{
  height:6px;
  left:0;
  right:0;
  top:5px;
  position:absolute; }

.bp3-slider-track{
  border-radius:3px;
  overflow:hidden; }

.bp3-slider-progress{
  background:rgba(92, 112, 128, 0.2); }
  .bp3-dark .bp3-slider-progress{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-slider-progress.bp3-intent-primary{
    background-color:#137cbd; }
  .bp3-slider-progress.bp3-intent-success{
    background-color:#0f9960; }
  .bp3-slider-progress.bp3-intent-warning{
    background-color:#d9822b; }
  .bp3-slider-progress.bp3-intent-danger{
    background-color:#db3737; }

.bp3-slider-handle{
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  color:#182026;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
  cursor:pointer;
  height:16px;
  left:0;
  position:absolute;
  top:0;
  width:16px; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
  .bp3-slider-handle:active, .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
  .bp3-slider-handle:disabled, .bp3-slider-handle.bp3-disabled{
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed;
    outline:none; }
    .bp3-slider-handle:disabled.bp3-active, .bp3-slider-handle:disabled.bp3-active:hover, .bp3-slider-handle.bp3-disabled.bp3-active, .bp3-slider-handle.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }
  .bp3-slider-handle:focus{
    z-index:1; }
  .bp3-slider-handle:hover{
    background-clip:padding-box;
    background-color:#ebf1f5;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
    cursor:-webkit-grab;
    cursor:grab;
    z-index:2; }
  .bp3-slider-handle.bp3-active{
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-disabled .bp3-slider-handle{
    background:#bfccd6;
    -webkit-box-shadow:none;
            box-shadow:none;
    pointer-events:none; }
  .bp3-dark .bp3-slider-handle{
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover, .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover{
      background-color:#30404d;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#202b33;
      background-image:none;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-slider-handle:disabled, .bp3-dark .bp3-slider-handle.bp3-disabled{
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-slider-handle:disabled.bp3-active, .bp3-dark .bp3-slider-handle.bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-slider-handle .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-slider-handle, .bp3-dark .bp3-slider-handle:hover{
      background-color:#394b59; }
    .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#293742; }
  .bp3-dark .bp3-disabled .bp3-slider-handle{
    background:#5c7080;
    border-color:#5c7080;
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-slider-handle .bp3-slider-label{
    background:#394b59;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    color:#f5f8fa;
    margin-left:8px; }
    .bp3-dark .bp3-slider-handle .bp3-slider-label{
      background:#e1e8ed;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
      color:#394b59; }
    .bp3-disabled .bp3-slider-handle .bp3-slider-label{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-slider-handle.bp3-start, .bp3-slider-handle.bp3-end{
    width:8px; }
  .bp3-slider-handle.bp3-start{
    border-bottom-right-radius:0;
    border-top-right-radius:0; }
  .bp3-slider-handle.bp3-end{
    border-bottom-left-radius:0;
    border-top-left-radius:0;
    margin-left:8px; }
    .bp3-slider-handle.bp3-end .bp3-slider-label{
      margin-left:0; }

.bp3-slider-label{
  -webkit-transform:translate(-50%, 20px);
          transform:translate(-50%, 20px);
  display:inline-block;
  font-size:12px;
  line-height:1;
  padding:2px 5px;
  position:absolute;
  vertical-align:top; }

.bp3-slider.bp3-vertical{
  height:150px;
  min-width:40px;
  width:40px; }
  .bp3-slider.bp3-vertical .bp3-slider-track,
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    bottom:0;
    height:auto;
    left:5px;
    top:0;
    width:6px; }
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    top:auto; }
  .bp3-slider.bp3-vertical .bp3-slider-label{
    -webkit-transform:translate(20px, 50%);
            transform:translate(20px, 50%); }
  .bp3-slider.bp3-vertical .bp3-slider-handle{
    top:auto; }
    .bp3-slider.bp3-vertical .bp3-slider-handle .bp3-slider-label{
      margin-left:0;
      margin-top:-8px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end, .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      height:8px;
      margin-left:0;
      width:16px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      border-bottom-right-radius:3px;
      border-top-left-radius:0; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start .bp3-slider-label{
        -webkit-transform:translate(20px);
                transform:translate(20px); }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end{
      border-bottom-left-radius:0;
      border-bottom-right-radius:0;
      border-top-left-radius:3px;
      margin-bottom:8px; }

@-webkit-keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

@keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

.bp3-spinner{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  overflow:visible;
  vertical-align:middle; }
  .bp3-spinner svg{
    display:block; }
  .bp3-spinner path{
    fill-opacity:0; }
  .bp3-spinner .bp3-spinner-head{
    stroke:rgba(92, 112, 128, 0.8);
    stroke-linecap:round;
    -webkit-transform-origin:center;
            transform-origin:center;
    -webkit-transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-spinner .bp3-spinner-track{
    stroke:rgba(92, 112, 128, 0.2); }

.bp3-spinner-animation{
  -webkit-animation:pt-spinner-animation 500ms linear infinite;
          animation:pt-spinner-animation 500ms linear infinite; }
  .bp3-no-spin > .bp3-spinner-animation{
    -webkit-animation:none;
            animation:none; }

.bp3-dark .bp3-spinner .bp3-spinner-head{
  stroke:#8a9ba8; }

.bp3-dark .bp3-spinner .bp3-spinner-track{
  stroke:rgba(16, 22, 26, 0.5); }

.bp3-spinner.bp3-intent-primary .bp3-spinner-head{
  stroke:#137cbd; }

.bp3-spinner.bp3-intent-success .bp3-spinner-head{
  stroke:#0f9960; }

.bp3-spinner.bp3-intent-warning .bp3-spinner-head{
  stroke:#d9822b; }

.bp3-spinner.bp3-intent-danger .bp3-spinner-head{
  stroke:#db3737; }
.bp3-tabs.bp3-vertical{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-tabs.bp3-vertical > .bp3-tab-list{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start;
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab{
      border-radius:3px;
      padding:0 10px;
      width:100%; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab[aria-selected="true"]{
        background-color:rgba(19, 124, 189, 0.2);
        -webkit-box-shadow:none;
                box-shadow:none; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab-indicator-wrapper .bp3-tab-indicator{
      background-color:rgba(19, 124, 189, 0.2);
      border-radius:3px;
      bottom:0;
      height:auto;
      left:0;
      right:0;
      top:0; }
  .bp3-tabs.bp3-vertical > .bp3-tab-panel{
    margin-top:0;
    padding-left:20px; }

.bp3-tab-list{
  -webkit-box-align:end;
      -ms-flex-align:end;
          align-items:flex-end;
  border:none;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  list-style:none;
  margin:0;
  padding:0;
  position:relative; }
  .bp3-tab-list > *:not(:last-child){
    margin-right:20px; }

.bp3-tab{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  color:#182026;
  cursor:pointer;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  font-size:14px;
  line-height:30px;
  max-width:100%;
  position:relative;
  vertical-align:top; }
  .bp3-tab a{
    color:inherit;
    display:block;
    text-decoration:none; }
  .bp3-tab-indicator-wrapper ~ .bp3-tab{
    background-color:transparent !important;
    -webkit-box-shadow:none !important;
            box-shadow:none !important; }
  .bp3-tab[aria-disabled="true"]{
    color:rgba(92, 112, 128, 0.6);
    cursor:not-allowed; }
  .bp3-tab[aria-selected="true"]{
    border-radius:0;
    -webkit-box-shadow:inset 0 -3px 0 #106ba3;
            box-shadow:inset 0 -3px 0 #106ba3; }
  .bp3-tab[aria-selected="true"], .bp3-tab:not([aria-disabled="true"]):hover{
    color:#106ba3; }
  .bp3-tab:focus{
    -moz-outline-radius:0; }
  .bp3-large > .bp3-tab{
    font-size:16px;
    line-height:40px; }

.bp3-tab-panel{
  margin-top:20px; }
  .bp3-tab-panel[aria-hidden="true"]{
    display:none; }

.bp3-tab-indicator-wrapper{
  left:0;
  pointer-events:none;
  position:absolute;
  top:0;
  -webkit-transform:translateX(0), translateY(0);
          transform:translateX(0), translateY(0);
  -webkit-transition:height, width, -webkit-transform;
  transition:height, width, -webkit-transform;
  transition:height, transform, width;
  transition:height, transform, width, -webkit-transform;
  -webkit-transition-duration:200ms;
          transition-duration:200ms;
  -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
          transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tab-indicator-wrapper .bp3-tab-indicator{
    background-color:#106ba3;
    bottom:0;
    height:3px;
    left:0;
    position:absolute;
    right:0; }
  .bp3-tab-indicator-wrapper.bp3-no-animation{
    -webkit-transition:none;
    transition:none; }

.bp3-dark .bp3-tab{
  color:#f5f8fa; }
  .bp3-dark .bp3-tab[aria-disabled="true"]{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tab[aria-selected="true"]{
    -webkit-box-shadow:inset 0 -3px 0 #48aff0;
            box-shadow:inset 0 -3px 0 #48aff0; }
  .bp3-dark .bp3-tab[aria-selected="true"], .bp3-dark .bp3-tab:not([aria-disabled="true"]):hover{
    color:#48aff0; }

.bp3-dark .bp3-tab-indicator{
  background-color:#48aff0; }

.bp3-flex-expander{
  -webkit-box-flex:1;
      -ms-flex:1 1;
          flex:1 1; }
.bp3-tag{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  background-color:#5c7080;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:none;
          box-shadow:none;
  color:#f5f8fa;
  font-size:12px;
  line-height:16px;
  max-width:100%;
  min-height:20px;
  min-width:20px;
  padding:2px 6px;
  position:relative; }
  .bp3-tag.bp3-interactive{
    cursor:pointer; }
    .bp3-tag.bp3-interactive:hover{
      background-color:rgba(92, 112, 128, 0.85); }
    .bp3-tag.bp3-interactive.bp3-active, .bp3-tag.bp3-interactive:active{
      background-color:rgba(92, 112, 128, 0.7); }
  .bp3-tag > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag::before,
  .bp3-tag > *{
    margin-right:4px; }
  .bp3-tag:empty::before,
  .bp3-tag > :last-child{
    margin-right:0; }
  .bp3-tag:focus{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:0;
    -moz-outline-radius:6px; }
  .bp3-tag.bp3-round{
    border-radius:30px;
    padding-left:8px;
    padding-right:8px; }
  .bp3-dark .bp3-tag{
    background-color:#bfccd6;
    color:#182026; }
    .bp3-dark .bp3-tag.bp3-interactive{
      cursor:pointer; }
      .bp3-dark .bp3-tag.bp3-interactive:hover{
        background-color:rgba(191, 204, 214, 0.85); }
      .bp3-dark .bp3-tag.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-interactive:active{
        background-color:rgba(191, 204, 214, 0.7); }
    .bp3-dark .bp3-tag > .bp3-icon, .bp3-dark .bp3-tag .bp3-icon-standard, .bp3-dark .bp3-tag .bp3-icon-large{
      fill:currentColor; }
  .bp3-tag > .bp3-icon, .bp3-tag .bp3-icon-standard, .bp3-tag .bp3-icon-large{
    fill:#ffffff; }
  .bp3-tag.bp3-large,
  .bp3-large .bp3-tag{
    font-size:14px;
    line-height:20px;
    min-height:30px;
    min-width:30px;
    padding:5px 10px; }
    .bp3-tag.bp3-large::before,
    .bp3-tag.bp3-large > *,
    .bp3-large .bp3-tag::before,
    .bp3-large .bp3-tag > *{
      margin-right:7px; }
    .bp3-tag.bp3-large:empty::before,
    .bp3-tag.bp3-large > :last-child,
    .bp3-large .bp3-tag:empty::before,
    .bp3-large .bp3-tag > :last-child{
      margin-right:0; }
    .bp3-tag.bp3-large.bp3-round,
    .bp3-large .bp3-tag.bp3-round{
      padding-left:12px;
      padding-right:12px; }
  .bp3-tag.bp3-intent-primary{
    background:#137cbd;
    color:#ffffff; }
    .bp3-tag.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.85); }
      .bp3-tag.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.7); }
  .bp3-tag.bp3-intent-success{
    background:#0f9960;
    color:#ffffff; }
    .bp3-tag.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.85); }
      .bp3-tag.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.7); }
  .bp3-tag.bp3-intent-warning{
    background:#d9822b;
    color:#ffffff; }
    .bp3-tag.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.85); }
      .bp3-tag.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.7); }
  .bp3-tag.bp3-intent-danger{
    background:#db3737;
    color:#ffffff; }
    .bp3-tag.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.85); }
      .bp3-tag.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.7); }
  .bp3-tag.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-tag.bp3-minimal > .bp3-icon, .bp3-tag.bp3-minimal .bp3-icon-standard, .bp3-tag.bp3-minimal .bp3-icon-large{
    fill:#5c7080; }
  .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
    background-color:rgba(138, 155, 168, 0.2);
    color:#182026; }
    .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
        background-color:rgba(92, 112, 128, 0.3); }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
        background-color:rgba(92, 112, 128, 0.4); }
    .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
      color:#f5f8fa; }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
          background-color:rgba(191, 204, 214, 0.3); }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
          background-color:rgba(191, 204, 214, 0.4); }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) > .bp3-icon, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-large{
        fill:#a7b6c2; }
  .bp3-tag.bp3-minimal.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15);
    color:#106ba3; }
    .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-primary > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-large{
      fill:#137cbd; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25);
      color:#48aff0; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15);
    color:#0d8050; }
    .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-success > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-large{
      fill:#0f9960; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25);
      color:#3dcc91; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15);
    color:#bf7326; }
    .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-warning > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-large{
      fill:#d9822b; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25);
      color:#ffb366; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15);
    color:#c23030; }
    .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-danger > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-large{
      fill:#db3737; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25);
      color:#ff7373; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.45); }

.bp3-tag-remove{
  background:none;
  border:none;
  color:inherit;
  cursor:pointer;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin-bottom:-2px;
  margin-right:-6px !important;
  margin-top:-2px;
  opacity:0.5;
  padding:2px;
  padding-left:0; }
  .bp3-tag-remove:hover{
    background:none;
    opacity:0.8;
    text-decoration:none; }
  .bp3-tag-remove:active{
    opacity:1; }
  .bp3-tag-remove:empty::before{
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-style:normal;
    font-weight:400;
    line-height:1;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    content:""; }
  .bp3-large .bp3-tag-remove{
    margin-right:-10px !important;
    padding:0 5px 0 0; }
    .bp3-large .bp3-tag-remove:empty::before{
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-style:normal;
      font-weight:400;
      line-height:1; }
.bp3-tag-input{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  cursor:text;
  height:auto;
  line-height:inherit;
  min-height:30px;
  padding-left:5px;
  padding-right:0; }
  .bp3-tag-input > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag-input > .bp3-tag-input-values{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag-input .bp3-tag-input-icon{
    color:#5c7080;
    margin-left:2px;
    margin-right:7px;
    margin-top:7px; }
  .bp3-tag-input .bp3-tag-input-values{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    -ms-flex-item-align:stretch;
        align-self:stretch;
    -ms-flex-wrap:wrap;
        flex-wrap:wrap;
    margin-right:7px;
    margin-top:5px;
    min-width:0; }
    .bp3-tag-input .bp3-tag-input-values > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag-input .bp3-tag-input-values > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag-input .bp3-tag-input-values::before,
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-right:5px; }
    .bp3-tag-input .bp3-tag-input-values:empty::before,
    .bp3-tag-input .bp3-tag-input-values > :last-child{
      margin-right:0; }
    .bp3-tag-input .bp3-tag-input-values:first-child .bp3-input-ghost:first-child{
      padding-left:5px; }
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-bottom:5px; }
  .bp3-tag-input .bp3-tag{
    overflow-wrap:break-word; }
    .bp3-tag-input .bp3-tag.bp3-active{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:0;
      -moz-outline-radius:6px; }
  .bp3-tag-input .bp3-input-ghost{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    line-height:20px;
    width:80px; }
    .bp3-tag-input .bp3-input-ghost:disabled, .bp3-tag-input .bp3-input-ghost.bp3-disabled{
      cursor:not-allowed; }
  .bp3-tag-input .bp3-button,
  .bp3-tag-input .bp3-spinner{
    margin:3px;
    margin-left:0; }
  .bp3-tag-input .bp3-button{
    min-height:24px;
    min-width:24px;
    padding:0 7px; }
  .bp3-tag-input.bp3-large{
    height:auto;
    min-height:40px; }
    .bp3-tag-input.bp3-large::before,
    .bp3-tag-input.bp3-large > *{
      margin-right:10px; }
    .bp3-tag-input.bp3-large:empty::before,
    .bp3-tag-input.bp3-large > :last-child{
      margin-right:0; }
    .bp3-tag-input.bp3-large .bp3-tag-input-icon{
      margin-left:5px;
      margin-top:10px; }
    .bp3-tag-input.bp3-large .bp3-input-ghost{
      line-height:30px; }
    .bp3-tag-input.bp3-large .bp3-button{
      min-height:30px;
      min-width:30px;
      padding:5px 10px;
      margin:5px;
      margin-left:0; }
    .bp3-tag-input.bp3-large .bp3-spinner{
      margin:8px;
      margin-left:0; }
  .bp3-tag-input.bp3-active{
    background-color:#ffffff;
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-tag-input .bp3-tag-input-icon, .bp3-tag-input.bp3-dark .bp3-tag-input-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-tag-input .bp3-input-ghost, .bp3-tag-input.bp3-dark .bp3-input-ghost{
    color:#f5f8fa; }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-webkit-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-moz-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost:-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::placeholder{
      color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tag-input.bp3-active, .bp3-tag-input.bp3-dark.bp3-active{
    background-color:rgba(16, 22, 26, 0.3);
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-primary, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-success, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-warning, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-danger, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-input-ghost{
  background:none;
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0; }
  .bp3-input-ghost::-webkit-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-moz-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::-ms-input-placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost::placeholder{
    color:rgba(92, 112, 128, 0.6);
    opacity:1; }
  .bp3-input-ghost:focus{
    outline:none !important; }
.bp3-toast{
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  margin:20px 0 0;
  max-width:500px;
  min-width:300px;
  pointer-events:all;
  position:relative !important; }
  .bp3-toast.bp3-toast-enter, .bp3-toast.bp3-toast-appear{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active, .bp3-toast.bp3-toast-appear-active{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-enter ~ .bp3-toast, .bp3-toast.bp3-toast-appear ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active ~ .bp3-toast, .bp3-toast.bp3-toast-appear-active ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11); }
  .bp3-toast.bp3-toast-exit{
    opacity:1;
    -webkit-filter:blur(0);
            filter:blur(0); }
  .bp3-toast.bp3-toast-exit-active{
    opacity:0;
    -webkit-filter:blur(10px);
            filter:blur(10px);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:opacity, filter;
    transition-property:opacity, filter, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast.bp3-toast-exit ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0); }
  .bp3-toast.bp3-toast-exit-active ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px);
    -webkit-transition-delay:50ms;
            transition-delay:50ms;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-toast .bp3-button-group{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    padding:5px;
    padding-left:0; }
  .bp3-toast > .bp3-icon{
    color:#5c7080;
    margin:12px;
    margin-right:0; }
  .bp3-toast.bp3-dark,
  .bp3-dark .bp3-toast{
    background-color:#394b59;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-toast.bp3-dark > .bp3-icon,
    .bp3-dark .bp3-toast > .bp3-icon{
      color:#a7b6c2; }
  .bp3-toast[class*="bp3-intent-"] a{
    color:rgba(255, 255, 255, 0.7); }
    .bp3-toast[class*="bp3-intent-"] a:hover{
      color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] > .bp3-icon{
    color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button, .bp3-toast[class*="bp3-intent-"] .bp3-button::before,
  .bp3-toast[class*="bp3-intent-"] .bp3-button .bp3-icon, .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    color:rgba(255, 255, 255, 0.7) !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:focus{
    outline-color:rgba(255, 255, 255, 0.5); }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:hover{
    background-color:rgba(255, 255, 255, 0.15) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    background-color:rgba(255, 255, 255, 0.3) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button::after{
    background:rgba(255, 255, 255, 0.3) !important; }
  .bp3-toast.bp3-intent-primary{
    background-color:#137cbd;
    color:#ffffff; }
  .bp3-toast.bp3-intent-success{
    background-color:#0f9960;
    color:#ffffff; }
  .bp3-toast.bp3-intent-warning{
    background-color:#d9822b;
    color:#ffffff; }
  .bp3-toast.bp3-intent-danger{
    background-color:#db3737;
    color:#ffffff; }

.bp3-toast-message{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  padding:11px;
  word-break:break-word; }

.bp3-toast-container{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box !important;
  display:-ms-flexbox !important;
  display:flex !important;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  left:0;
  overflow:hidden;
  padding:0 20px 20px;
  pointer-events:none;
  right:0;
  z-index:40; }
  .bp3-toast-container.bp3-toast-container-in-portal{
    position:fixed; }
  .bp3-toast-container.bp3-toast-container-inline{
    position:absolute; }
  .bp3-toast-container.bp3-toast-container-top{
    top:0; }
  .bp3-toast-container.bp3-toast-container-bottom{
    bottom:0;
    -webkit-box-orient:vertical;
    -webkit-box-direction:reverse;
        -ms-flex-direction:column-reverse;
            flex-direction:column-reverse;
    top:auto; }
  .bp3-toast-container.bp3-toast-container-left{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
  .bp3-toast-container.bp3-toast-container-right{
    -webkit-box-align:end;
        -ms-flex-align:end;
            align-items:flex-end; }

.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active) ~ .bp3-toast, .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active) ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-exit-active ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-leave-active ~ .bp3-toast{
  -webkit-transform:translateY(60px);
          transform:translateY(60px); }
.bp3-tooltip{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1); }
  .bp3-tooltip .bp3-popover-arrow{
    height:22px;
    position:absolute;
    width:22px; }
    .bp3-tooltip .bp3-popover-arrow::before{
      height:14px;
      margin:4px;
      width:14px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip{
    margin-bottom:11px;
    margin-top:-11px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
      bottom:-8px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip{
    margin-left:11px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
      left:-8px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip{
    margin-top:11px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
      top:-8px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip{
    margin-left:-11px;
    margin-right:11px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
      right:-8px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-tooltip > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-tooltip > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
    top:-0.22183px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
    right:-0.22183px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
    left:-0.22183px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
    bottom:-0.22183px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-tooltip .bp3-popover-content{
    background:#394b59;
    color:#f5f8fa; }
  .bp3-tooltip .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-tooltip .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-tooltip .bp3-popover-arrow-fill{
    fill:#394b59; }
  .bp3-popover-enter > .bp3-tooltip, .bp3-popover-appear > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8); }
  .bp3-popover-enter-active > .bp3-tooltip, .bp3-popover-appear-active > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-popover-exit > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8);
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tooltip .bp3-popover-content{
    padding:10px 12px; }
  .bp3-tooltip.bp3-dark,
  .bp3-dark .bp3-tooltip{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-tooltip .bp3-popover-content{
      background:#e1e8ed;
      color:#394b59; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-fill{
      fill:#e1e8ed; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-content{
    background:#137cbd;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-arrow-fill{
    fill:#137cbd; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-content{
    background:#0f9960;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-arrow-fill{
    fill:#0f9960; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-content{
    background:#d9822b;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-arrow-fill{
    fill:#d9822b; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-content{
    background:#db3737;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-arrow-fill{
    fill:#db3737; }

.bp3-tooltip-indicator{
  border-bottom:dotted 1px;
  cursor:help; }
.bp3-tree .bp3-icon, .bp3-tree .bp3-icon-standard, .bp3-tree .bp3-icon-large{
  color:#5c7080; }
  .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-tree .bp3-icon.bp3-intent-success, .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-tree-node-list{
  list-style:none;
  margin:0;
  padding-left:0; }

.bp3-tree-root{
  background-color:transparent;
  cursor:default;
  padding-left:0;
  position:relative; }

.bp3-tree-node-content-0{
  padding-left:0px; }

.bp3-tree-node-content-1{
  padding-left:23px; }

.bp3-tree-node-content-2{
  padding-left:46px; }

.bp3-tree-node-content-3{
  padding-left:69px; }

.bp3-tree-node-content-4{
  padding-left:92px; }

.bp3-tree-node-content-5{
  padding-left:115px; }

.bp3-tree-node-content-6{
  padding-left:138px; }

.bp3-tree-node-content-7{
  padding-left:161px; }

.bp3-tree-node-content-8{
  padding-left:184px; }

.bp3-tree-node-content-9{
  padding-left:207px; }

.bp3-tree-node-content-10{
  padding-left:230px; }

.bp3-tree-node-content-11{
  padding-left:253px; }

.bp3-tree-node-content-12{
  padding-left:276px; }

.bp3-tree-node-content-13{
  padding-left:299px; }

.bp3-tree-node-content-14{
  padding-left:322px; }

.bp3-tree-node-content-15{
  padding-left:345px; }

.bp3-tree-node-content-16{
  padding-left:368px; }

.bp3-tree-node-content-17{
  padding-left:391px; }

.bp3-tree-node-content-18{
  padding-left:414px; }

.bp3-tree-node-content-19{
  padding-left:437px; }

.bp3-tree-node-content-20{
  padding-left:460px; }

.bp3-tree-node-content{
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  height:30px;
  padding-right:5px;
  width:100%; }
  .bp3-tree-node-content:hover{
    background-color:rgba(191, 204, 214, 0.4); }

.bp3-tree-node-caret,
.bp3-tree-node-caret-none{
  min-width:30px; }

.bp3-tree-node-caret{
  color:#5c7080;
  cursor:pointer;
  padding:7px;
  -webkit-transform:rotate(0deg);
          transform:rotate(0deg);
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tree-node-caret:hover{
    color:#182026; }
  .bp3-dark .bp3-tree-node-caret{
    color:#a7b6c2; }
    .bp3-dark .bp3-tree-node-caret:hover{
      color:#f5f8fa; }
  .bp3-tree-node-caret.bp3-tree-node-caret-open{
    -webkit-transform:rotate(90deg);
            transform:rotate(90deg); }
  .bp3-tree-node-caret.bp3-icon-standard::before{
    content:""; }

.bp3-tree-node-icon{
  margin-right:7px;
  position:relative; }

.bp3-tree-node-label{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-label span{
    display:inline; }

.bp3-tree-node-secondary-label{
  padding:0 5px;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-secondary-label .bp3-popover-wrapper,
  .bp3-tree-node-secondary-label .bp3-popover-target{
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-content{
  background-color:inherit;
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-caret,
.bp3-tree-node.bp3-disabled .bp3-tree-node-icon{
  color:rgba(92, 112, 128, 0.6);
  cursor:not-allowed; }

.bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content,
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-standard, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-large{
    color:#ffffff; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret::before{
    color:rgba(255, 255, 255, 0.7); }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret:hover::before{
    color:#ffffff; }

.bp3-dark .bp3-tree-node-content:hover{
  background-color:rgba(92, 112, 128, 0.3); }

.bp3-dark .bp3-tree .bp3-icon, .bp3-dark .bp3-tree .bp3-icon-standard, .bp3-dark .bp3-tree .bp3-icon-large{
  color:#a7b6c2; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-dark .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
.bp3-omnibar{
  -webkit-filter:blur(0);
          filter:blur(0);
  opacity:1;
  background-color:#ffffff;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  left:calc(50% - 250px);
  top:20vh;
  width:500px;
  z-index:21; }
  .bp3-omnibar.bp3-overlay-enter, .bp3-omnibar.bp3-overlay-appear{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2; }
  .bp3-omnibar.bp3-overlay-enter-active, .bp3-omnibar.bp3-overlay-appear-active{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar.bp3-overlay-exit{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1; }
  .bp3-omnibar.bp3-overlay-exit-active{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2;
    -webkit-transition-delay:0;
            transition-delay:0;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-omnibar .bp3-input{
    background-color:transparent;
    border-radius:0; }
    .bp3-omnibar .bp3-input, .bp3-omnibar .bp3-input:focus{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-omnibar .bp3-menu{
    background-color:transparent;
    border-radius:0;
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
    max-height:calc(60vh - 40px);
    overflow:auto; }
    .bp3-omnibar .bp3-menu:empty{
      display:none; }
  .bp3-dark .bp3-omnibar, .bp3-omnibar.bp3-dark{
    background-color:#30404d;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-omnibar-overlay .bp3-overlay-backdrop{
  background-color:rgba(16, 22, 26, 0.2); }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }

.bp3-multi-select{
  min-width:150px; }

.bp3-multi-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto; }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-height:300px;
  max-width:400px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1pY29uLWJyYW5kMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNmZmYiPgogICAgPHBhdGggZD0iTTEwNSAxMjcuM2g0MHYxMi44aC00MHpNNTEuMSA3N0w3NCA5OS45bC0yMy4zIDIzLjMgMTAuNSAxMC41IDIzLjMtMjMuM0w5NSA5OS45IDg0LjUgODkuNCA2MS42IDY2LjV6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNGOUE4MjUiPgogICAgPHBhdGggZD0iTTIwLjIgMTEuOGMtMS42IDAtMS43LjUtMS43IDEgMCAuNC4xLjkuMSAxLjMuMS41LjEuOS4xIDEuMyAwIDEuNy0xLjQgMi4zLTMuNSAyLjNoLS45di0xLjloLjVjMS4xIDAgMS40IDAgMS40LS44IDAtLjMgMC0uNi0uMS0xIDAtLjQtLjEtLjgtLjEtMS4yIDAtMS4zIDAtMS44IDEuMy0yLTEuMy0uMi0xLjMtLjctMS4zLTIgMC0uNC4xLS44LjEtMS4yLjEtLjQuMS0uNy4xLTEgMC0uOC0uNC0uNy0xLjQtLjhoLS41VjQuMWguOWMyLjIgMCAzLjUuNyAzLjUgMi4zIDAgLjQtLjEuOS0uMSAxLjMtLjEuNS0uMS45LS4xIDEuMyAwIC41LjIgMSAxLjcgMXYxLjh6TTEuOCAxMC4xYzEuNiAwIDEuNy0uNSAxLjctMSAwLS40LS4xLS45LS4xLTEuMy0uMS0uNS0uMS0uOS0uMS0xLjMgMC0xLjYgMS40LTIuMyAzLjUtMi4zaC45djEuOWgtLjVjLTEgMC0xLjQgMC0xLjQuOCAwIC4zIDAgLjYuMSAxIDAgLjIuMS42LjEgMSAwIDEuMyAwIDEuOC0xLjMgMkM2IDExLjIgNiAxMS43IDYgMTNjMCAuNC0uMS44LS4xIDEuMi0uMS4zLS4xLjctLjEgMSAwIC44LjMuOCAxLjQuOGguNXYxLjloLS45Yy0yLjEgMC0zLjUtLjYtMy41LTIuMyAwLS40LjEtLjkuMS0xLjMuMS0uNS4xLS45LjEtMS4zIDAtLjUtLjItMS0xLjctMXYtMS45eiIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSIxMy44IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY3g9IjExIiBjeT0iOC4yIiByPSIyLjEiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgPGcgY2xhc3M9ImpwLWljb24td2FybjAiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4=);
  --jp-icon-listings-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MC45NzggNTAuOTc4IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCA1MC45NzggNTAuOTc4OyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+Cgk8Zz4KCQk8cGF0aCBzdHlsZT0iZmlsbDojMDEwMDAyOyIgZD0iTTQzLjUyLDcuNDU4QzM4LjcxMSwyLjY0OCwzMi4zMDcsMCwyNS40ODksMEMxOC42NywwLDEyLjI2NiwyLjY0OCw3LjQ1OCw3LjQ1OAoJCQljLTkuOTQzLDkuOTQxLTkuOTQzLDI2LjExOSwwLDM2LjA2MmM0LjgwOSw0LjgwOSwxMS4yMTIsNy40NTYsMTguMDMxLDcuNDU4YzAsMCwwLjAwMSwwLDAuMDAyLDAKCQkJYzYuODE2LDAsMTMuMjIxLTIuNjQ4LDE4LjAyOS03LjQ1OGM0LjgwOS00LjgwOSw3LjQ1Ny0xMS4yMTIsNy40NTctMTguMDNDNTAuOTc3LDE4LjY3LDQ4LjMyOCwxMi4yNjYsNDMuNTIsNy40NTh6CgkJCSBNNDIuMTA2LDQyLjEwNWMtNC40MzIsNC40MzEtMTAuMzMyLDYuODcyLTE2LjYxNSw2Ljg3MmgtMC4wMDJjLTYuMjg1LTAuMDAxLTEyLjE4Ny0yLjQ0MS0xNi42MTctNi44NzIKCQkJYy05LjE2Mi05LjE2My05LjE2Mi0yNC4wNzEsMC0zMy4yMzNDMTMuMzAzLDQuNDQsMTkuMjA0LDIsMjUuNDg5LDJjNi4yODQsMCwxMi4xODYsMi40NCwxNi42MTcsNi44NzIKCQkJYzQuNDMxLDQuNDMxLDYuODcxLDEwLjMzMiw2Ljg3MSwxNi42MTdDNDguOTc3LDMxLjc3Miw0Ni41MzYsMzcuNjc1LDQyLjEwNiw0Mi4xMDV6Ii8+CgkJPHBhdGggc3R5bGU9ImZpbGw6IzAxMDAwMjsiIGQ9Ik0yMy41NzgsMzIuMjE4Yy0wLjAyMy0xLjczNCwwLjE0My0zLjA1OSwwLjQ5Ni0zLjk3MmMwLjM1My0wLjkxMywxLjExLTEuOTk3LDIuMjcyLTMuMjUzCgkJCWMwLjQ2OC0wLjUzNiwwLjkyMy0xLjA2MiwxLjM2Ny0xLjU3NWMwLjYyNi0wLjc1MywxLjEwNC0xLjQ3OCwxLjQzNi0yLjE3NWMwLjMzMS0wLjcwNywwLjQ5NS0xLjU0MSwwLjQ5NS0yLjUKCQkJYzAtMS4wOTYtMC4yNi0yLjA4OC0wLjc3OS0yLjk3OWMtMC41NjUtMC44NzktMS41MDEtMS4zMzYtMi44MDYtMS4zNjljLTEuODAyLDAuMDU3LTIuOTg1LDAuNjY3LTMuNTUsMS44MzIKCQkJYy0wLjMwMSwwLjUzNS0wLjUwMywxLjE0MS0wLjYwNywxLjgxNGMtMC4xMzksMC43MDctMC4yMDcsMS40MzItMC4yMDcsMi4xNzRoLTIuOTM3Yy0wLjA5MS0yLjIwOCwwLjQwNy00LjExNCwxLjQ5My01LjcxOQoJCQljMS4wNjItMS42NCwyLjg1NS0yLjQ4MSw1LjM3OC0yLjUyN2MyLjE2LDAuMDIzLDMuODc0LDAuNjA4LDUuMTQxLDEuNzU4YzEuMjc4LDEuMTYsMS45MjksMi43NjQsMS45NSw0LjgxMQoJCQljMCwxLjE0Mi0wLjEzNywyLjExMS0wLjQxLDIuOTExYy0wLjMwOSwwLjg0NS0wLjczMSwxLjU5My0xLjI2OCwyLjI0M2MtMC40OTIsMC42NS0xLjA2OCwxLjMxOC0xLjczLDIuMDAyCgkJCWMtMC42NSwwLjY5Ny0xLjMxMywxLjQ3OS0xLjk4NywyLjM0NmMtMC4yMzksMC4zNzctMC40MjksMC43NzctMC41NjUsMS4xOTljLTAuMTYsMC45NTktMC4yMTcsMS45NTEtMC4xNzEsMi45NzkKCQkJQzI2LjU4OSwzMi4yMTgsMjMuNTc4LDMyLjIxOCwyMy41NzgsMzIuMjE4eiBNMjMuNTc4LDM4LjIydi0zLjQ4NGgzLjA3NnYzLjQ4NEgyMy41Nzh6Ii8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMEQ0N0ExIj4KICAgIDxwYXRoIGQ9Ik0xMS4xIDYuOVY1LjhINi45YzAtLjUgMC0xLjMuMi0xLjYuNC0uNy44LTEuMSAxLjctMS40IDEuNy0uMyAyLjUtLjMgMy45LS4xIDEgLjEgMS45LjkgMS45IDEuOXY0LjJjMCAuNS0uOSAxLjYtMiAxLjZIOC44Yy0xLjUgMC0yLjQgMS40LTIuNCAyLjh2Mi4ySDQuN0MzLjUgMTUuMSAzIDE0IDMgMTMuMVY5Yy0uMS0xIC42LTIgMS44LTIgMS41LS4xIDYuMy0uMSA2LjMtLjF6Ii8+CiAgICA8cGF0aCBkPSJNMTAuOSAxNS4xdjEuMWg0LjJjMCAuNSAwIDEuMy0uMiAxLjYtLjQuNy0uOCAxLjEtMS43IDEuNC0xLjcuMy0yLjUuMy0zLjkuMS0xLS4xLTEuOS0uOS0xLjktMS45di00LjJjMC0uNS45LTEuNiAyLTEuNmgzLjhjMS41IDAgMi40LTEuNCAyLjQtMi44VjYuNmgxLjdDMTguNSA2LjkgMTkgOCAxOSA4LjlWMTNjMCAxLS43IDIuMS0xLjkgMi4xaC02LjJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMikiIGZpbGw9IiMzMzMzMzMiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uLWFjY2VudDIganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGQ9Ik01LjA1NjY0IDguNzYxNzJDNS4wNTY2NCA4LjU5NzY2IDUuMDMxMjUgOC40NTMxMiA0Ljk4MDQ3IDguMzI4MTJDNC45MzM1OSA4LjE5OTIyIDQuODU1NDcgOC4wODIwMyA0Ljc0NjA5IDcuOTc2NTZDNC42NDA2MiA3Ljg3MTA5IDQuNSA3Ljc3NTM5IDQuMzI0MjIgNy42ODk0NUM0LjE1MjM0IDcuNTk5NjEgMy45NDMzNiA3LjUxMTcyIDMuNjk3MjcgNy40MjU3OEMzLjMwMjczIDcuMjg1MTYgMi45NDMzNiA3LjEzNjcyIDIuNjE5MTQgNi45ODA0N0MyLjI5NDkyIDYuODI0MjIgMi4wMTc1OCA2LjY0MjU4IDEuNzg3MTEgNi40MzU1NUMxLjU2MDU1IDYuMjI4NTIgMS4zODQ3NyA1Ljk4ODI4IDEuMjU5NzcgNS43MTQ4NEMxLjEzNDc3IDUuNDM3NSAxLjA3MjI3IDUuMTA5MzggMS4wNzIyNyA0LjczMDQ3QzEuMDcyMjcgNC4zOTg0NCAxLjEyODkxIDQuMDk1NyAxLjI0MjE5IDMuODIyMjdDMS4zNTU0NyAzLjU0NDkyIDEuNTE1NjIgMy4zMDQ2OSAxLjcyMjY2IDMuMTAxNTZDMS45Mjk2OSAyLjg5ODQ0IDIuMTc5NjkgMi43MzQzNyAyLjQ3MjY2IDIuNjA5MzhDMi43NjU2MiAyLjQ4NDM4IDMuMDkxOCAyLjQwNDMgMy40NTExNyAyLjM2OTE0VjEuMTA5MzhINC4zODg2N1YyLjM4MDg2QzQuNzQwMjMgMi40Mjc3MyA1LjA1NjY0IDIuNTIzNDQgNS4zMzc4OSAyLjY2Nzk3QzUuNjE5MTQgMi44MTI1IDUuODU3NDIgMy4wMDE5NSA2LjA1MjczIDMuMjM2MzNDNi4yNTE5NSAzLjQ2NjggNi40MDQzIDMuNzQwMjMgNi41MDk3NyA0LjA1NjY0QzYuNjE5MTQgNC4zNjkxNCA2LjY3MzgzIDQuNzIwNyA2LjY3MzgzIDUuMTExMzNINS4wNDQ5MkM1LjA0NDkyIDQuNjM4NjcgNC45Mzc1IDQuMjgxMjUgNC43MjI2NiA0LjAzOTA2QzQuNTA3ODEgMy43OTI5NyA0LjIxNjggMy42Njk5MiAzLjg0OTYxIDMuNjY5OTJDMy42NTAzOSAzLjY2OTkyIDMuNDc2NTYgMy42OTcyNyAzLjMyODEyIDMuNzUxOTVDMy4xODM1OSAzLjgwMjczIDMuMDY0NDUgMy44NzY5NSAyLjk3MDcgMy45NzQ2MUMyLjg3Njk1IDQuMDY4MzYgMi44MDY2NCA0LjE3OTY5IDIuNzU5NzcgNC4zMDg1OUMyLjcxNjggNC40Mzc1IDIuNjk1MzEgNC41NzgxMiAyLjY5NTMxIDQuNzMwNDdDMi42OTUzMSA0Ljg4MjgxIDIuNzE2OCA1LjAxOTUzIDIuNzU5NzcgNS4xNDA2MkMyLjgwNjY0IDUuMjU3ODEgMi44ODI4MSA1LjM2NzE5IDIuOTg4MjggNS40Njg3NUMzLjA5NzY2IDUuNTcwMzEgMy4yNDAyMyA1LjY2Nzk3IDMuNDE2MDIgNS43NjE3MkMzLjU5MTggNS44NTE1NiAzLjgxMDU1IDUuOTQzMzYgNC4wNzIyNyA2LjAzNzExQzQuNDY2OCA2LjE4NTU1IDQuODI0MjIgNi4zMzk4NCA1LjE0NDUzIDYuNUM1LjQ2NDg0IDYuNjU2MjUgNS43MzgyOCA2LjgzOTg0IDUuOTY0ODQgNy4wNTA3OEM2LjE5NTMxIDcuMjU3ODEgNi4zNzEwOSA3LjUgNi40OTIxOSA3Ljc3NzM0QzYuNjE3MTkgOC4wNTA3OCA2LjY3OTY5IDguMzc1IDYuNjc5NjkgOC43NUM2LjY3OTY5IDkuMDkzNzUgNi42MjMwNSA5LjQwNDMgNi41MDk3NyA5LjY4MTY0QzYuMzk2NDggOS45NTUwOCA2LjIzNDM4IDEwLjE5MTQgNi4wMjM0NCAxMC4zOTA2QzUuODEyNSAxMC41ODk4IDUuNTU4NTkgMTAuNzUgNS4yNjE3MiAxMC44NzExQzQuOTY0ODQgMTAuOTg4MyA0LjYzMjgxIDExLjA2NDUgNC4yNjU2MiAxMS4wOTk2VjEyLjI0OEgzLjMzMzk4VjExLjA5OTZDMy4wMDE5NSAxMS4wNjg0IDIuNjc5NjkgMTAuOTk2MSAyLjM2NzE5IDEwLjg4MjhDMi4wNTQ2OSAxMC43NjU2IDEuNzc3MzQgMTAuNTk3NyAxLjUzNTE2IDEwLjM3ODlDMS4yOTY4OCAxMC4xNjAyIDEuMTA1NDcgOS44ODQ3NyAwLjk2MDkzOCA5LjU1MjczQzAuODE2NDA2IDkuMjE2OCAwLjc0NDE0MSA4LjgxNDQ1IDAuNzQ0MTQxIDguMzQ1N0gyLjM3ODkxQzIuMzc4OTEgOC42MjY5NSAyLjQxOTkyIDguODYzMjggMi41MDE5NSA5LjA1NDY5QzIuNTgzOTggOS4yNDIxOSAyLjY4OTQ1IDkuMzkyNTggMi44MTgzNiA5LjUwNTg2QzIuOTUxMTcgOS42MTUyMyAzLjEwMTU2IDkuNjkzMzYgMy4yNjk1MyA5Ljc0MDIzQzMuNDM3NSA5Ljc4NzExIDMuNjA5MzggOS44MTA1NSAzLjc4NTE2IDkuODEwNTVDNC4yMDMxMiA5LjgxMDU1IDQuNTE5NTMgOS43MTI4OSA0LjczNDM4IDkuNTE3NThDNC45NDkyMiA5LjMyMjI3IDUuMDU2NjQgOS4wNzAzMSA1LjA1NjY0IDguNzYxNzJaTTEzLjQxOCAxMi4yNzE1SDguMDc0MjJWMTFIMTMuNDE4VjEyLjI3MTVaIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzLjk1MjY0IDYpIiBmaWxsPSJ3aGl0ZSIvPgo8L3N2Zz4K);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTUgMTVIM3YyaDEydi0yem0wLThIM3YyaDEyVjd6TTMgMTNoMTh2LTJIM3Yyem0wIDhoMTh2LTJIM3Yyek0zIDN2MmgxOFYzSDN6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4=);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}
.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}
.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}
.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}
.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}
.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}
.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}
.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}
.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}
.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}
.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}
.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}
.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}
.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}
.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}
.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}
.jp-CodeIcon {
  background-image: var(--jp-icon-code);
}
.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}
.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}
.jp-CopyrightIcon {
  background-image: var(--jp-icon-copyright);
}
.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}
.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}
.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}
.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}
.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}
.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}
.jp-FileIcon {
  background-image: var(--jp-icon-file);
}
.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}
.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}
.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}
.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}
.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}
.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}
.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}
.jp-JuliaIcon {
  background-image: var(--jp-icon-julia);
}
.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}
.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}
.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}
.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}
.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}
.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}
.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}
.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}
.jp-ListIcon {
  background-image: var(--jp-icon-list);
}
.jp-ListingsInfoIcon {
  background-image: var(--jp-icon-listings-info);
}
.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}
.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}
.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}
.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}
.jp-NumberingIcon {
  background-image: var(--jp-icon-numbering);
}
.jp-OfflineBoltIcon {
  background-image: var(--jp-icon-offline-bolt);
}
.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}
.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}
.jp-PdfIcon {
  background-image: var(--jp-icon-pdf);
}
.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}
.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}
.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}
.jp-RedoIcon {
  background-image: var(--jp-icon-redo);
}
.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}
.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}
.jp-RunIcon {
  background-image: var(--jp-icon-run);
}
.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}
.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}
.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}
.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}
.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}
.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}
.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}
.jp-TableRowsIcon {
  background-image: var(--jp-icon-table-rows);
}
.jp-TagIcon {
  background-image: var(--jp-icon-tag);
}
.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}
.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}
.jp-TocIcon {
  background-image: var(--jp-icon-toc);
}
.jp-TreeViewIcon {
  background-image: var(--jp-icon-tree-view);
}
.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}
.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}
.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}
.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}
/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}
/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}
/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}
.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}
.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}
.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}
.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}
.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}
.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}
.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}
.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}
/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}
.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}
.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}
.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}
.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}
.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}
.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}
/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

/* CSS for icons in selected items in the settings editor */
#setting-editor .jp-PluginList .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
#setting-editor
  .jp-PluginList
  .jp-mod-selected
  .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected tabs in the sidebar tab manager */
#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable[fill] {
  fill: #fff;
}

#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable[fill] {
  fill: var(--jp-brand-color1);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable-inverse[fill] {
  fill: #fff;
}

/**
 * TODO: come up with non css-hack solution for showing the busy icon on top
 *  of the close icon
 * CSS for complex behavior of close icon of tabs in the sidebar tab manager
 */
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-dirty.jp-mod-active
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: #fff;
}

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) svg {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-switch {
  display: flex;
  align-items: center;
  padding-left: 4px;
  padding-right: 4px;
  font-size: var(--jp-ui-font-size1);
  background-color: transparent;
  color: var(--jp-ui-font-color1);
  border: none;
  height: 20px;
}

.jp-switch:hover {
  background-color: var(--jp-layout-color2);
}

.jp-switch-label {
  margin-right: 5px;
}

.jp-switch-track {
  cursor: pointer;
  background-color: var(--jp-border-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
  height: 16px;
  width: 35px;
  position: relative;
}

.jp-switch-track::before {
  content: '';
  position: absolute;
  height: 10px;
  width: 10px;
  margin: 3px;
  left: 0px;
  background-color: var(--jp-ui-inverse-font-color1);
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

.jp-switch[aria-checked='true'] .jp-switch-track {
  background-color: var(--jp-warn-color0);
}

.jp-switch[aria-checked='true'] .jp-switch-track::before {
  /* track width (35) - margins (3 + 3) - thumb width (10) */
  left: 19px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

/* Override Blueprint's _reset.scss styles */
html {
  box-sizing: unset;
}

*,
*::before,
*::after {
  box-sizing: unset;
}

body {
  color: unset;
  font-family: var(--jp-ui-font-family);
}

p {
  margin-top: unset;
  margin-bottom: unset;
}

small {
  font-size: unset;
}

strong {
  font-weight: unset;
}

/* Override Blueprint's _typography.scss styles */
a {
  text-decoration: unset;
  color: unset;
}
a:hover {
  text-decoration: unset;
  color: unset;
}

/* Override Blueprint's _accessibility.scss styles */
:focus {
  outline: unset;
  outline-offset: unset;
  -moz-outline-radius: unset;
}

/* Styles for ui-components */
.jp-Button {
  border-radius: var(--jp-border-radius);
  padding: 0px 12px;
  font-size: var(--jp-ui-font-size1);
}

/* Use our own theme for hover styles */
button.jp-Button.bp3-button.bp3-minimal:hover {
  background-color: var(--jp-layout-color2);
}
.jp-Button.minimal {
  color: unset !important;
}

.jp-Button.jp-ToolbarButtonComponent {
  text-transform: none;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color3);
}

.jp-BPIcon {
  display: inline-block;
  vertical-align: middle;
  margin: auto;
}

/* Stop blueprint futzing with our icon fills */
.bp3-icon.jp-BPIcon > svg:not([fill]) {
  fill: var(--jp-inverse-layout-color3);
}

.jp-InputGroupAction {
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

/* Use our own theme for hover and option styles */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}
select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-top: 1px solid var(--jp-border-color2);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-Collapse-header {
  padding: 1px 12px;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size2);
}

.jp-Collapse-header:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Collapse-contents {
  padding: 0px 12px 0px 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0px;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Modal variant
|----------------------------------------------------------------------------*/

.jp-ModalCommandPalette {
  position: absolute;
  z-index: 10000;
  top: 38px;
  left: 30%;
  margin: 0;
  padding: 4px;
  width: 40%;
  box-shadow: var(--jp-elevation-z4);
  border-radius: 4px;
  background: var(--jp-layout-color0);
}

.jp-ModalCommandPalette .lm-CommandPalette {
  max-height: 40vh;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
  display: none;
}

.jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
  margin-left: 4px;
  margin-right: 4px;
}

.jp-ModalCommandPalette
  .lm-CommandPalette
  .lm-CommandPalette-item.lm-mod-disabled {
  display: none;
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0px 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-SearchIconGroup {
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  padding: 5px 5px 1px 5px;
}

.jp-SearchIconGroup svg {
  height: 20px;
  width: 20px;
}

.jp-SearchIconGroup .jp-icon3[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color2);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0px;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item.lm-mod-active {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
  fill: var(--jp-layout-color0);
}

.lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-inverse-font-color0);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color2);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.6;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty:after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0px 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0px;
  left: 0px;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px;
  padding-bottom: 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
  resize: both;
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0px;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

button.jp-Dialog-close-button {
  padding: 0;
  height: 100%;
  min-width: unset;
  min-height: unset;
}

.jp-Dialog-header {
  display: flex;
  justify-content: space-between;
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0px 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

.jp-HoverBox.jp-mod-outofview {
  display: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

.jp-Input-Boolean-Dialog {
  flex-direction: row-reverse;
  align-items: end;
  width: 100%;
}

.jp-Input-Boolean-Dialog > label {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;

  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;

  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #aa00ff;

  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;

  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;

  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;

  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;

  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;

  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;

  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;

  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;

  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;

  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ffff00;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;

  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;

  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;

  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;

  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;

  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eeeeee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;

  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent:before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent:after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0px 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input[type='checkbox'].jp-mod-styled {
  appearance: checkbox;
  -webkit-appearance: checkbox;
  -moz-appearance: checkbox;
  height: auto;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-FileDialog-Checkbox {
  margin-top: 35px;
  display: flex;
  flex-direction: row;
  align-items: end;
  width: 100%;
}

.jp-FileDialog-Checkbox > label {
  flex: 1 1 auto;
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  height: 28px;
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  background-color: var(--jp-layout-color1);
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0px 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  height: 32px;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 1;
  overflow-x: auto;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px;
  margin: 0px;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px 6px;
  margin: 0px;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent span {
  padding: 0px;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar.jp-Toolbar-micro {
  padding: 0;
  min-height: 0;
}

#jp-main-dock-panel[data-mode='single-document']
  .jp-MainAreaWidget
  > .jp-Toolbar {
  border: none;
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ body.p-mod-override-cursor *, /* </DEPRECATED> */
body.lm-mod-override-cursor * {
  cursor: inherit !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/* BASICS */

.CodeMirror {
  /* Set height, width, borders, and global font properties here */
  font-family: monospace;
  height: 300px;
  color: black;
  direction: ltr;
}

/* PADDING */

.CodeMirror-lines {
  padding: 4px 0; /* Vertical padding around content */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  padding: 0 4px; /* Horizontal padding of content */
}

.CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  background-color: white; /* The little square between H and V scrollbars */
}

/* GUTTER */

.CodeMirror-gutters {
  border-right: 1px solid #ddd;
  background-color: #f7f7f7;
  white-space: nowrap;
}
.CodeMirror-linenumbers {}
.CodeMirror-linenumber {
  padding: 0 3px 0 5px;
  min-width: 20px;
  text-align: right;
  color: #999;
  white-space: nowrap;
}

.CodeMirror-guttermarker { color: black; }
.CodeMirror-guttermarker-subtle { color: #999; }

/* CURSOR */

.CodeMirror-cursor {
  border-left: 1px solid black;
  border-right: none;
  width: 0;
}
/* Shown when moving in bi-directional text */
.CodeMirror div.CodeMirror-secondarycursor {
  border-left: 1px solid silver;
}
.cm-fat-cursor .CodeMirror-cursor {
  width: auto;
  border: 0 !important;
  background: #7e7;
}
.cm-fat-cursor div.CodeMirror-cursors {
  z-index: 1;
}
.cm-fat-cursor-mark {
  background-color: rgba(20, 255, 20, 0.5);
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
}
.cm-animate-fat-cursor {
  width: auto;
  border: 0;
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
  background-color: #7e7;
}
@-moz-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@-webkit-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}

/* Can style cursor different in overwrite (non-insert) mode */
.CodeMirror-overwrite .CodeMirror-cursor {}

.cm-tab { display: inline-block; text-decoration: inherit; }

.CodeMirror-rulers {
  position: absolute;
  left: 0; right: 0; top: -50px; bottom: 0;
  overflow: hidden;
}
.CodeMirror-ruler {
  border-left: 1px solid #ccc;
  top: 0; bottom: 0;
  position: absolute;
}

/* DEFAULT THEME */

.cm-s-default .cm-header {color: blue;}
.cm-s-default .cm-quote {color: #090;}
.cm-negative {color: #d44;}
.cm-positive {color: #292;}
.cm-header, .cm-strong {font-weight: bold;}
.cm-em {font-style: italic;}
.cm-link {text-decoration: underline;}
.cm-strikethrough {text-decoration: line-through;}

.cm-s-default .cm-keyword {color: #708;}
.cm-s-default .cm-atom {color: #219;}
.cm-s-default .cm-number {color: #164;}
.cm-s-default .cm-def {color: #00f;}
.cm-s-default .cm-variable,
.cm-s-default .cm-punctuation,
.cm-s-default .cm-property,
.cm-s-default .cm-operator {}
.cm-s-default .cm-variable-2 {color: #05a;}
.cm-s-default .cm-variable-3, .cm-s-default .cm-type {color: #085;}
.cm-s-default .cm-comment {color: #a50;}
.cm-s-default .cm-string {color: #a11;}
.cm-s-default .cm-string-2 {color: #f50;}
.cm-s-default .cm-meta {color: #555;}
.cm-s-default .cm-qualifier {color: #555;}
.cm-s-default .cm-builtin {color: #30a;}
.cm-s-default .cm-bracket {color: #997;}
.cm-s-default .cm-tag {color: #170;}
.cm-s-default .cm-attribute {color: #00c;}
.cm-s-default .cm-hr {color: #999;}
.cm-s-default .cm-link {color: #00c;}

.cm-s-default .cm-error {color: #f00;}
.cm-invalidchar {color: #f00;}

.CodeMirror-composing { border-bottom: 2px solid; }

/* Default styles for common addons */

div.CodeMirror span.CodeMirror-matchingbracket {color: #0b0;}
div.CodeMirror span.CodeMirror-nonmatchingbracket {color: #a22;}
.CodeMirror-matchingtag { background: rgba(255, 150, 0, .3); }
.CodeMirror-activeline-background {background: #e8f2ff;}

/* STOP */

/* The rest of this file contains styles related to the mechanics of
   the editor. You probably shouldn't touch them. */

.CodeMirror {
  position: relative;
  overflow: hidden;
  background: white;
}

.CodeMirror-scroll {
  overflow: scroll !important; /* Things will break if this is overridden */
  /* 50px is the magic margin used to hide the element's real scrollbars */
  /* See overflow: hidden in .CodeMirror */
  margin-bottom: -50px; margin-right: -50px;
  padding-bottom: 50px;
  height: 100%;
  outline: none; /* Prevent dragging from highlighting the element */
  position: relative;
}
.CodeMirror-sizer {
  position: relative;
  border-right: 50px solid transparent;
}

/* The fake, visible scrollbars. Used to force redraw during scrolling
   before actual scrolling happens, thus preventing shaking and
   flickering artifacts. */
.CodeMirror-vscrollbar, .CodeMirror-hscrollbar, .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  position: absolute;
  z-index: 6;
  display: none;
  outline: none;
}
.CodeMirror-vscrollbar {
  right: 0; top: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}
.CodeMirror-hscrollbar {
  bottom: 0; left: 0;
  overflow-y: hidden;
  overflow-x: scroll;
}
.CodeMirror-scrollbar-filler {
  right: 0; bottom: 0;
}
.CodeMirror-gutter-filler {
  left: 0; bottom: 0;
}

.CodeMirror-gutters {
  position: absolute; left: 0; top: 0;
  min-height: 100%;
  z-index: 3;
}
.CodeMirror-gutter {
  white-space: normal;
  height: 100%;
  display: inline-block;
  vertical-align: top;
  margin-bottom: -50px;
}
.CodeMirror-gutter-wrapper {
  position: absolute;
  z-index: 4;
  background: none !important;
  border: none !important;
}
.CodeMirror-gutter-background {
  position: absolute;
  top: 0; bottom: 0;
  z-index: 4;
}
.CodeMirror-gutter-elt {
  position: absolute;
  cursor: default;
  z-index: 4;
}
.CodeMirror-gutter-wrapper ::selection { background-color: transparent }
.CodeMirror-gutter-wrapper ::-moz-selection { background-color: transparent }

.CodeMirror-lines {
  cursor: text;
  min-height: 1px; /* prevents collapsing before first draw */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  /* Reset some styles that the rest of the page might have set */
  -moz-border-radius: 0; -webkit-border-radius: 0; border-radius: 0;
  border-width: 0;
  background: transparent;
  font-family: inherit;
  font-size: inherit;
  margin: 0;
  white-space: pre;
  word-wrap: normal;
  line-height: inherit;
  color: inherit;
  z-index: 2;
  position: relative;
  overflow: visible;
  -webkit-tap-highlight-color: transparent;
  -webkit-font-variant-ligatures: contextual;
  font-variant-ligatures: contextual;
}
.CodeMirror-wrap pre.CodeMirror-line,
.CodeMirror-wrap pre.CodeMirror-line-like {
  word-wrap: break-word;
  white-space: pre-wrap;
  word-break: normal;
}

.CodeMirror-linebackground {
  position: absolute;
  left: 0; right: 0; top: 0; bottom: 0;
  z-index: 0;
}

.CodeMirror-linewidget {
  position: relative;
  z-index: 2;
  padding: 0.1px; /* Force widget margins to stay inside of the container */
}

.CodeMirror-widget {}

.CodeMirror-rtl pre { direction: rtl; }

.CodeMirror-code {
  outline: none;
}

/* Force content-box sizing for the elements where we expect it */
.CodeMirror-scroll,
.CodeMirror-sizer,
.CodeMirror-gutter,
.CodeMirror-gutters,
.CodeMirror-linenumber {
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}

.CodeMirror-measure {
  position: absolute;
  width: 100%;
  height: 0;
  overflow: hidden;
  visibility: hidden;
}

.CodeMirror-cursor {
  position: absolute;
  pointer-events: none;
}
.CodeMirror-measure pre { position: static; }

div.CodeMirror-cursors {
  visibility: hidden;
  position: relative;
  z-index: 3;
}
div.CodeMirror-dragcursors {
  visibility: visible;
}

.CodeMirror-focused div.CodeMirror-cursors {
  visibility: visible;
}

.CodeMirror-selected { background: #d9d9d9; }
.CodeMirror-focused .CodeMirror-selected { background: #d7d4f0; }
.CodeMirror-crosshair { cursor: crosshair; }
.CodeMirror-line::selection, .CodeMirror-line > span::selection, .CodeMirror-line > span > span::selection { background: #d7d4f0; }
.CodeMirror-line::-moz-selection, .CodeMirror-line > span::-moz-selection, .CodeMirror-line > span > span::-moz-selection { background: #d7d4f0; }

.cm-searching {
  background-color: #ffa;
  background-color: rgba(255, 255, 0, .4);
}

/* Used to force a border model for a node */
.cm-force-border { padding-right: .1px; }

@media print {
  /* Hide the cursor when printing */
  .CodeMirror div.CodeMirror-cursors {
    visibility: hidden;
  }
}

/* See issue #2901 */
.cm-tab-wrap-hack:after { content: ''; }

/* Help users use markselection to safely style text background */
span.CodeMirror-selectedtext { background: none; }

.CodeMirror-dialog {
  position: absolute;
  left: 0; right: 0;
  background: inherit;
  z-index: 15;
  padding: .1em .8em;
  overflow: hidden;
  color: inherit;
}

.CodeMirror-dialog-top {
  border-bottom: 1px solid #eee;
  top: 0;
}

.CodeMirror-dialog-bottom {
  border-top: 1px solid #eee;
  bottom: 0;
}

.CodeMirror-dialog input {
  border: none;
  outline: none;
  background: transparent;
  width: 20em;
  color: inherit;
  font-family: monospace;
}

.CodeMirror-dialog button {
  font-size: 70%;
}

.CodeMirror-foldmarker {
  color: blue;
  text-shadow: #b9f 1px 1px 2px, #b9f -1px -1px 2px, #b9f 1px -1px 2px, #b9f -1px 1px 2px;
  font-family: arial;
  line-height: .3;
  cursor: pointer;
}
.CodeMirror-foldgutter {
  width: .7em;
}
.CodeMirror-foldgutter-open,
.CodeMirror-foldgutter-folded {
  cursor: pointer;
}
.CodeMirror-foldgutter-open:after {
  content: "\25BE";
}
.CodeMirror-foldgutter-folded:after {
  content: "\25B8";
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.CodeMirror {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;
  /* Changed to auto to autogrow */
}

.CodeMirror pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* This causes https://github.com/jupyter/jupyterlab/issues/522 */
/* May not cause it not because we changed it! */
.CodeMirror-lines {
  padding: var(--jp-code-padding) 0;
}

.CodeMirror-linenumber {
  padding: 0 8px;
}

.jp-CodeMirrorEditor {
  cursor: text;
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.CodeMirror.jp-mod-readOnly .CodeMirror-cursor {
  display: none;
}

.CodeMirror-gutters {
  border-right: 1px solid var(--jp-border-color2);
  background-color: var(--jp-layout-color0);
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.CodeMirror-selectedtext.cm-searching {
  background-color: var(--jp-search-selected-match-background-color) !important;
  color: var(--jp-search-selected-match-color) !important;
}

.cm-searching {
  background-color: var(
    --jp-search-unselected-match-background-color
  ) !important;
  color: var(--jp-search-unselected-match-color) !important;
}

.CodeMirror-focused .CodeMirror-selected {
  background-color: var(--jp-editor-selected-focused-background);
}

.CodeMirror-selected {
  background-color: var(--jp-editor-selected-background);
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/**
 * Here is our jupyter theme for CodeMirror syntax highlighting
 * This is used in our marked.js syntax highlighting and CodeMirror itself
 * The string "jupyter" is set in ../codemirror/widget.DEFAULT_CODEMIRROR_THEME
 * This came from the classic notebook, which came form highlight.js/GitHub
 */

/**
 * CodeMirror themes are handling the background/color in this way. This works
 * fine for CodeMirror editors outside the notebook, but the notebook styles
 * these things differently.
 */
.CodeMirror.cm-s-jupyter {
  background: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* In the notebook, we want this styling to be handled by its container */
.jp-CodeConsole .CodeMirror.cm-s-jupyter,
.jp-Notebook .CodeMirror.cm-s-jupyter {
  background: transparent;
}

.cm-s-jupyter .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}
.cm-s-jupyter span.cm-keyword {
  color: var(--jp-mirror-editor-keyword-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-atom {
  color: var(--jp-mirror-editor-atom-color);
}
.cm-s-jupyter span.cm-number {
  color: var(--jp-mirror-editor-number-color);
}
.cm-s-jupyter span.cm-def {
  color: var(--jp-mirror-editor-def-color);
}
.cm-s-jupyter span.cm-variable {
  color: var(--jp-mirror-editor-variable-color);
}
.cm-s-jupyter span.cm-variable-2 {
  color: var(--jp-mirror-editor-variable-2-color);
}
.cm-s-jupyter span.cm-variable-3 {
  color: var(--jp-mirror-editor-variable-3-color);
}
.cm-s-jupyter span.cm-punctuation {
  color: var(--jp-mirror-editor-punctuation-color);
}
.cm-s-jupyter span.cm-property {
  color: var(--jp-mirror-editor-property-color);
}
.cm-s-jupyter span.cm-operator {
  color: var(--jp-mirror-editor-operator-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-comment {
  color: var(--jp-mirror-editor-comment-color);
  font-style: italic;
}
.cm-s-jupyter span.cm-string {
  color: var(--jp-mirror-editor-string-color);
}
.cm-s-jupyter span.cm-string-2 {
  color: var(--jp-mirror-editor-string-2-color);
}
.cm-s-jupyter span.cm-meta {
  color: var(--jp-mirror-editor-meta-color);
}
.cm-s-jupyter span.cm-qualifier {
  color: var(--jp-mirror-editor-qualifier-color);
}
.cm-s-jupyter span.cm-builtin {
  color: var(--jp-mirror-editor-builtin-color);
}
.cm-s-jupyter span.cm-bracket {
  color: var(--jp-mirror-editor-bracket-color);
}
.cm-s-jupyter span.cm-tag {
  color: var(--jp-mirror-editor-tag-color);
}
.cm-s-jupyter span.cm-attribute {
  color: var(--jp-mirror-editor-attribute-color);
}
.cm-s-jupyter span.cm-header {
  color: var(--jp-mirror-editor-header-color);
}
.cm-s-jupyter span.cm-quote {
  color: var(--jp-mirror-editor-quote-color);
}
.cm-s-jupyter span.cm-link {
  color: var(--jp-mirror-editor-link-color);
}
.cm-s-jupyter span.cm-error {
  color: var(--jp-mirror-editor-error-color);
}
.cm-s-jupyter span.cm-hr {
  color: #999;
}

.cm-s-jupyter span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}

.cm-s-jupyter .CodeMirror-activeline-background,
.cm-s-jupyter .CodeMirror-gutter {
  background-color: var(--jp-layout-color2);
}

/* Styles for shared cursors (remote cursor locations and selected ranges) */
.jp-CodeMirrorEditor .remote-caret {
  position: relative;
  border-left: 2px solid black;
  margin-left: -1px;
  margin-right: -1px;
  box-sizing: border-box;
}

.jp-CodeMirrorEditor .remote-caret > div {
  white-space: nowrap;
  position: absolute;
  top: -1.15em;
  padding-bottom: 0.05em;
  left: -2px;
  font-size: 0.95em;
  background-color: rgb(250, 129, 0);
  font-family: var(--jp-ui-font-family);
  font-weight: bold;
  line-height: normal;
  user-select: none;
  color: white;
  padding-left: 2px;
  padding-right: 2px;
  z-index: 3;
  transition: opacity 0.3s ease-in-out;
}

.jp-CodeMirrorEditor .remote-caret.hide-name > div {
  transition-delay: 0.7s;
  opacity: 0;
}

.jp-CodeMirrorEditor .remote-caret:hover > div {
  opacity: 1;
  transition-delay: 0s;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

:root {
  /* This is the padding value to fill the gaps between lines containing spans with background color. */
  --jp-private-code-span-padding: calc(
    (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
  );
}

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0px;
  padding: 0px;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}
.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}
.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}
.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}
.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}
.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}
.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}
.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}
.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}
.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}
.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}
.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}
.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}
.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}
.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
  padding: var(--jp-private-code-span-padding) 0;
}
.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}
.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
  padding: var(--jp-private-code-span-padding) 0;
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}
.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0em;
}

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: 12px;
  table-layout: fixed;
  margin-left: auto;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon table {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0px;
}

.jp-RenderedHTMLCommon p {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}
/* ...or leave it untouched if they don't */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-dark-background {
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-light-background {
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}
.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}
.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}
.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}
.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}
.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}
.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}
.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}
.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: 0.8em;
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser {
  display: flex;
  flex-direction: column;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  border-bottom: none;
  height: auto;
  margin: var(--jp-toolbar-header-margin);
  box-shadow: none;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 8px 12px 8px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0px 2px;
  padding: 0px 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0px;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar.jp-Toolbar {
  padding: 0px;
  margin: 8px 12px 0px 12px;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  justify-content: flex-start;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-Toolbar-item {
  flex: 0 0 auto;
  padding-left: 0px;
  padding-right: 2px;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-ToolbarButtonComponent {
  width: 40px;
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent {
  width: 72px;
  background: var(--jp-brand-color1);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent:focus-visible {
  background-color: var(--jp-brand-color0);
}

.jp-FileBrowser-toolbar.jp-Toolbar
  .jp-Toolbar-item:first-child
  .jp-ToolbarButtonComponent
  .jp-icon3 {
  fill: white;
}

/*-----------------------------------------------------------------------------
| Other styles
|----------------------------------------------------------------------------*/

.jp-FileDialog.jp-mod-conflict input {
  color: var(--jp-error-color1);
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

.jp-LastModified-hidden {
  display: none;
}

.jp-FileBrowser-filterBox {
  padding: 0px;
  flex: 0 0 auto;
  margin: 8px 12px 0px 12px;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing:focus-visible {
  border: 1px solid var(--jp-brand-color1);
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px 12px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-id-narrow {
  display: none;
  flex: 0 0 5px;
  padding: 4px 4px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
  color: var(--jp-border-color2);
}

.jp-DirListing-narrow .jp-id-narrow {
  display: block;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-DirListing-content mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
  color: var(--jp-ui-inverse-font-color0);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-item[data-is-dot] {
  opacity: 75%;
}

.jp-DirListing-item.jp-mod-selected {
  color: var(--jp-ui-inverse-font-color1);
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon:before {
  color: var(--jp-success-color1);
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.jp-mod-running.jp-mod-selected
  .jp-DirListing-itemIcon:before {
  color: var(--jp-ui-inverse-font-color1);
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0px;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-DirListing-deadSpace {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
}

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: flex;
  flex-direction: row;
}

body[data-format='mobile'] .jp-OutputArea-child {
  flex-direction: column;
}

.jp-OutputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-OutputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

.jp-OutputArea-output {
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea-child .jp-OutputArea-output {
  flex-grow: 1;
  flex-shrink: 1;
}

body[data-format='mobile'] .jp-OutputArea-child .jp-OutputArea-output {
  margin-left: var(--jp-notebook-padding);
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0px;
  padding: 0px;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0px;
  flex: 1 1 auto;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
  border-top: var(--jp-border-width) solid transparent;
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-OutputArea-stdin {
  line-height: var(--jp-code-line-height);
  padding-top: var(--jp-code-padding);
  display: flex;
}

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;
  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0px;
  bottom: 0px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0px;
  width: 100%;
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: flex;
  flex-direction: row;
  overflow: hidden;
}

body[data-format='mobile'] .jp-InputArea {
  flex-direction: column;
}

.jp-InputArea-editor {
  flex: 1 1 auto;
  overflow: hidden;
}

.jp-InputArea-editor {
  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0px;
  background: var(--jp-cell-editor-background);
}

body[data-format='mobile'] .jp-InputArea-editor {
  margin-left: var(--jp-notebook-padding);
}

.jp-InputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

body[data-format='mobile'] .jp-InputPrompt {
  flex: 0 0 auto;
  text-align: left;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: flex;
  flex-direction: row;
  flex: 1 1 auto;
}

.jp-Placeholder-prompt {
  box-sizing: border-box;
}

.jp-Placeholder-content {
  flex: 1 1 auto;
  border: none;
  background: transparent;
  height: 20px;
  box-sizing: border-box;
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0px;
  margin: 0px;
  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 200px;
  box-shadow: inset 0 0 6px 2px rgba(0, 0, 0, 0.3);
  margin-left: var(--jp-private-cell-scrolling-output-offset);
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  flex: 0 0
    calc(
      var(--jp-cell-prompt-width) -
        var(--jp-private-cell-scrolling-output-offset)
    );
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  flex: 1 1 auto;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

.jp-showHiddenCellsButton {
  margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
  margin-top: var(--jp-code-padding);
  border: 1px solid var(--jp-border-color2);
  background-color: var(--jp-border-color3) !important;
  color: var(--jp-content-font-color0) !important;
}

.jp-showHiddenCellsButton:hover {
  background-color: var(--jp-border-color2) !important;
}

.jp-collapseHeadingButton {
  display: none;
}

.jp-MarkdownCell:hover .jp-collapseHeadingButton {
  display: flex;
  min-height: var(--jp-cell-collapser-min-height);
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: 2px;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-MainAreaWidget-ContainStrict .jp-Notebook * {
  contain: strict;
}

.jp-Notebook-render * {
  contain: none !important;
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
  float: left;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* cell is dirty */
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
  color: var(--jp-warn-color1);
}
.jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt:before {
  color: var(--jp-warn-color1);
  content: '•';
}

.jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
  background: var(--jp-warn-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: block;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0px;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-NotebookTools-tool {
  padding: 0px 12px 0 12px;
}

.jp-ActiveCellTool {
  padding: 12px;
  background-color: var(--jp-layout-color1);
  border-top: none !important;
}

.jp-ActiveCellTool .jp-InputArea-prompt {
  flex: 0 0 auto;
  padding-left: 0px;
}

.jp-ActiveCellTool .jp-InputArea-editor {
  flex: 1 1 auto;
  background: var(--jp-cell-editor-background);
  border-color: var(--jp-cell-editor-border-color);
}

.jp-ActiveCellTool .jp-InputArea-editor .CodeMirror {
  background: transparent;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0px 12px 0px;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label {
  line-height: 1.4;
}

.jp-NotebookTools .jp-select-wrapper {
  margin-top: 4px;
  margin-bottom: 0px;
}

.jp-NotebookTools .jp-Collapse {
  margin-top: 16px;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Cell-Placeholder {
  padding-left: 55px;
}

.jp-Cell-Placeholder-wrapper {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  margin: 10px 15px;
}

.jp-Cell-Placeholder-wrapper-inner {
  padding: 15px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body {
  background-repeat: repeat;
  background-size: 50% auto;
}

.jp-Cell-Placeholder-wrapper-body div {
  background: #f6f7f8;
  background-image: -webkit-linear-gradient(
    left,
    #f6f7f8 0%,
    #edeef1 20%,
    #f6f7f8 40%,
    #f6f7f8 100%
  );
  background-repeat: no-repeat;
  background-size: 800px 104px;
  height: 104px;
  position: relative;
}

.jp-Cell-Placeholder-wrapper-body div {
  position: absolute;
  right: 15px;
  left: 15px;
  top: 15px;
}

div.jp-Cell-Placeholder-h1 {
  top: 20px;
  height: 20px;
  left: 15px;
  width: 150px;
}

div.jp-Cell-Placeholder-h2 {
  left: 15px;
  top: 50px;
  height: 10px;
  width: 100px;
}

div.jp-Cell-Placeholder-content-1,
div.jp-Cell-Placeholder-content-2,
div.jp-Cell-Placeholder-content-3 {
  left: 15px;
  right: 15px;
  height: 10px;
}

div.jp-Cell-Placeholder-content-1 {
  top: 100px;
}

div.jp-Cell-Placeholder-content-2 {
  top: 120px;
}

div.jp-Cell-Placeholder-content-3 {
  top: 140px;
}

</style>

    <style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0px 2px 1px -1px var(--jp-shadow-umbra-color),
    0px 1px 1px 0px var(--jp-shadow-penumbra-color),
    0px 1px 3px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0px 3px 1px -2px var(--jp-shadow-umbra-color),
    0px 2px 2px 0px var(--jp-shadow-penumbra-color),
    0px 1px 5px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0px 2px 4px -1px var(--jp-shadow-umbra-color),
    0px 4px 5px 0px var(--jp-shadow-penumbra-color),
    0px 1px 10px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0px 3px 5px -1px var(--jp-shadow-umbra-color),
    0px 6px 10px 0px var(--jp-shadow-penumbra-color),
    0px 1px 18px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0px 5px 5px -3px var(--jp-shadow-umbra-color),
    0px 8px 10px 1px var(--jp-shadow-penumbra-color),
    0px 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0px 7px 8px -4px var(--jp-shadow-umbra-color),
    0px 12px 17px 2px var(--jp-shadow-penumbra-color),
    0px 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0px 8px 10px -5px var(--jp-shadow-umbra-color),
    0px 16px 24px 2px var(--jp-shadow-penumbra-color),
    0px 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0px 10px 13px -6px var(--jp-shadow-umbra-color),
    0px 20px 31px 3px var(--jp-shadow-penumbra-color),
    0px 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0px 11px 15px -7px var(--jp-shadow-umbra-color),
    0px 24px 38px 3px var(--jp-shadow-penumbra-color),
    0px 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;

  --jp-ui-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica,
    Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;

  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);

  --jp-content-link-color: var(--md-blue-700);

  --jp-content-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: Menlo, Consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-900);
  --jp-brand-color1: var(--md-blue-700);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);

  --jp-accent-color0: var(--md-green-900);
  --jp-accent-color1: var(--md-green-700);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-900);
  --jp-warn-color1: var(--md-orange-700);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);

  --jp-error-color0: var(--md-red-900);
  --jp-error-color1: var(--md-red-700);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);

  --jp-success-color0: var(--md-green-900);
  --jp-success-color1: var(--md-green-700);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);

  --jp-info-color0: var(--md-cyan-900);
  --jp-info-color1: var(--md-cyan-700);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;

  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;

  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);

  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
  --jp-cell-prompt-letter-spacing: 0px;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);
  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;
  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0px 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Statusbar specific styles */

  --jp-statusbar-height: 24px;

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-border-color1);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: #05a;
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #aa22ff;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #aa22ff;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 250px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);
}
</style>

<style type="text/css">
/* Force rendering true colors when outputing to pdf */
* {
  -webkit-print-color-adjust: exact;
}

/* Misc */
a.anchor-link {
  display: none;
}

/* Input area styling */
.jp-InputArea {
  overflow: hidden;
}

.jp-InputArea-editor {
  overflow: hidden;
}

.CodeMirror.cm-s-jupyter .highlight pre {
/* weird, but --jp-code-padding defined to be 5px but 4px horizontal padding is hardcoded for pre.CodeMirror-line */
  padding: var(--jp-code-padding) 4px;
  margin: 0;

  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
  color: inherit;

}

.jp-OutputArea-output pre {
  line-height: inherit;
  font-family: inherit;
}

.jp-RenderedText pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
}

/* Using table instead of flexbox so that we can use break-inside property */
/* CSS rules under this comment should not be required anymore after we move to the JupyterLab 4.0 CSS */


.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  min-width: calc(
    var(--jp-cell-prompt-width) - var(--jp-private-cell-scrolling-output-offset)
  );
}

.jp-OutputArea-child {
  display: table;
  width: 100%;
}

.jp-OutputPrompt {
  display: table-cell;
  vertical-align: top;
  min-width: var(--jp-cell-prompt-width);
}

body[data-format='mobile'] .jp-OutputPrompt {
  display: table-row;
}

.jp-OutputArea-output {
  display: table-cell;
  width: 100%;
}

body[data-format='mobile'] .jp-OutputArea-child .jp-OutputArea-output {
  display: table-row;
}

.jp-OutputArea-output.jp-OutputArea-executeResult {
  width: 100%;
}

/* Hiding the collapser by default */
.jp-Collapser {
  display: none;
}

@page {
    margin: 0.5in; /* Margin for each printed piece of paper */
}

@media print {
  .jp-Cell-inputWrapper,
  .jp-Cell-outputWrapper {
    display: block;
  }

  .jp-OutputArea-child {
    break-inside: avoid-page;
  }
}
</style>

<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: {
                    automatic: true
                    }
                }
            });

            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
    <!-- End of mathjax configuration --></head>
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">

<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h1 id="Covid-19-Death-and-Vaccination-EDA-(Worldwide)">Covid 19 Death and Vaccination EDA (Worldwide)<a class="anchor-link" href="#Covid-19-Death-and-Vaccination-EDA-(Worldwide)">&#182;</a></h1><h3 id="1/22/2020---2/15/2023">1/22/2020 - 2/15/2023<a class="anchor-link" href="#1/22/2020---2/15/2023">&#182;</a></h3>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Lets-take-a-look-at-the-raw-global-data-tables-from-Johns's-Hopkins-(Kaggle)">Lets take a look at the raw global data tables from Johns's Hopkins (Kaggle)<a class="anchor-link" href="#Lets-take-a-look-at-the-raw-global-data-tables-from-Johns's-Hopkins-(Kaggle)">&#182;</a></h4>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>Province/State</th>
      <th>Lat</th>
      <th>Long</th>
      <th>1/22/20</th>
      <th>1/23/20</th>
      <th>1/24/20</th>
      <th>1/25/20</th>
      <th>1/26/20</th>
      <th>1/27/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>NaN</td>
      <td>33.93911</td>
      <td>67.709953</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>NaN</td>
      <td>41.15330</td>
      <td>20.168300</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>NaN</td>
      <td>28.03390</td>
      <td>1.659600</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>NaN</td>
      <td>42.50630</td>
      <td>1.521800</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>NaN</td>
      <td>-11.20270</td>
      <td>17.873900</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1125 columns</p>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Each column is a country, but we can see by scrolling over that not all of them are countries. for example there is a &quot;winter olympics 2022&quot; column, so some of the columns are well known events.</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>&lt;class &#39;pandas.core.frame.DataFrame&#39;&gt;
RangeIndex: 289 entries, 0 to 288
Columns: 1125 entries, Country/Region to 2/15/23
dtypes: float64(2), int64(1121), object(2)
memory usage: 2.5+ MB
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--1124 rows, each row is covid deaths reported for a country.<br />
--1121 of the columns are int64, so the death data is numeric, no need to convert it</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan</th>
      <td>1120.0</td>
      <td>7.050000</td>
      <td>15.765575</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>6.0</td>
      <td>159.0</td>
    </tr>
    <tr>
      <th>Albania</th>
      <td>1120.0</td>
      <td>3.210714</td>
      <td>4.491106</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>5.0</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Algeria</th>
      <td>1120.0</td>
      <td>6.143750</td>
      <td>7.482828</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>9.0</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th>Andorra</th>
      <td>1120.0</td>
      <td>0.147321</td>
      <td>0.537006</td>
      <td>-2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>Angola</th>
      <td>1120.0</td>
      <td>1.724107</td>
      <td>3.068149</td>
      <td>-3.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>West Bank and Gaza</th>
      <td>1120.0</td>
      <td>5.096429</td>
      <td>11.075240</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>7.0</td>
      <td>268.0</td>
    </tr>
    <tr>
      <th>Winter Olympics 2022</th>
      <td>1120.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>Yemen</th>
      <td>1120.0</td>
      <td>1.927679</td>
      <td>4.421608</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>60.0</td>
    </tr>
    <tr>
      <th>Zambia</th>
      <td>1120.0</td>
      <td>3.616964</td>
      <td>9.663354</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>72.0</td>
    </tr>
    <tr>
      <th>Zimbabwe</th>
      <td>1120.0</td>
      <td>5.055357</td>
      <td>12.746254</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>107.0</td>
    </tr>
  </tbody>
</table>
<p>198 rows × 8 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total</th>
      <th>Percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Province/State</th>
      <td>198</td>
      <td>0.685121</td>
    </tr>
    <tr>
      <th>Lat</th>
      <td>2</td>
      <td>0.006920</td>
    </tr>
    <tr>
      <th>Long</th>
      <td>2</td>
      <td>0.006920</td>
    </tr>
    <tr>
      <th>Country/Region</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2/4/22</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2/3/21</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2/4/21</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2/5/21</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2/6/21</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2/15/23</th>
      <td>0</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>1125 rows × 2 columns</p>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--lets remove the provice/state columns - there is a lot of missing data there, but could cause issues too, we will have to check</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>--------number of single country records, and number of provincial records---------
False    201
True      88
dtype: int64
--------number of records per country---------
Country/Region
Australia          8
Canada            16
China             34
Denmark            3
France            12
Netherlands        5
New Zealand        3
United Kingdom    15
dtype: int64
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>some of the data is in provincial format, some is single value for the country</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Lat</th>
      <th>Long</th>
      <th>1/22/20</th>
      <th>1/23/20</th>
      <th>1/24/20</th>
      <th>1/25/20</th>
      <th>1/26/20</th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
    <tr>
      <th>Country/Region</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan</th>
      <td>33.93911</td>
      <td>67.709953</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>Albania</th>
      <td>41.15330</td>
      <td>20.168300</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>Algeria</th>
      <td>28.03390</td>
      <td>1.659600</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>Andorra</th>
      <td>42.50630</td>
      <td>1.521800</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
      <td>165</td>
    </tr>
    <tr>
      <th>Angola</th>
      <td>-11.20270</td>
      <td>17.873900</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1123 columns</p>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--If we scroll to the right, we can see that the count is cumulative. to get the deaths per day, we would need to substract day from final day</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>1/30/20</th>
      <th>1/31/20</th>
      <th>2/1/20</th>
      <th>2/2/20</th>
      <th>2/3/20</th>
      <th>2/4/20</th>
      <th>2/5/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1116 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>1/30/20</th>
      <th>1/31/20</th>
      <th>2/1/20</th>
      <th>2/2/20</th>
      <th>2/3/20</th>
      <th>2/4/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>2/15/23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1117 columns</p>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--We need to drop that most recent day since we cant calculate a value form the cumulative sum for that day</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>1/27/20</th>
      <th>1/28/20</th>
      <th>1/29/20</th>
      <th>1/30/20</th>
      <th>1/31/20</th>
      <th>2/1/20</th>
      <th>2/2/20</th>
      <th>2/3/20</th>
      <th>2/4/20</th>
      <th>...</th>
      <th>2/6/23</th>
      <th>2/7/23</th>
      <th>2/8/23</th>
      <th>2/9/23</th>
      <th>2/10/23</th>
      <th>2/11/23</th>
      <th>2/12/23</th>
      <th>2/13/23</th>
      <th>2/14/23</th>
      <th>total_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7896</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3596</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>6881</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>165</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1931</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 1117 columns</p>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country/Region</th>
      <th>total_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>76</th>
      <td>Holy See</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Antarctica</td>
      <td>0</td>
    </tr>
    <tr>
      <th>185</th>
      <td>Tuvalu</td>
      <td>0</td>
    </tr>
    <tr>
      <th>197</th>
      <td>Winter Olympics 2022</td>
      <td>0</td>
    </tr>
    <tr>
      <th>170</th>
      <td>Summer Olympics 2020</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--We can see there are at least two &quot;events&quot; (the olympics), good to be aware of. We will leave them in for now.</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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e/bsydhn2bJlmj59urZt26aKFStq1KhRd/T3BgAAkF0ouwAAQK5w/RLC4ODgW+6za9cuxcbGavTo0cqXL5/y58+v0aNHa//+/fr555/v6DhlypRR69at5eXlpfr166tIkSJ/uih9s2bNlD9/fuXPn1+NGzeW3W7X5s2bJUlr1qxRaGioSpUqJUnauHGjmjZtmunjW7ZsqbCwMD3yyCN6+OGHNXr0aD3//PMaNGiQJGn16tUqW7asOnfuLB8fH5UrV049evTQp59+KklaunSpOnbsqKpVq8rHx0edO3fWX//615tmXbZsmXr16qVKlSrJ29tbLVq0UMOGDbV06dKMfdq3b6/SpUvL399fERERLMgPAADcjrILAADkCkWKFJEknT59+qbPJyQkKDExUUFBQcqbN2/G9rx586pgwYI6efKkS8e5zsfHRw6H45b7Fy1aNOPPvr6+Cg8P16pVqyRJK1asULt27SRJly5dUkxMjGrXrp3p41evXq1du3bp66+/VvPmzXXhwgU9+eST8va+tlrFyZMntXfvXoWFhWX89+abb+q3336TJP36668KCQnJ9Dmvl2t/lJCQcMNz9913X6a/m9+Xid7e3nI6nbd87QAAADmBsgsAAOQKISEhqlChgtatW3fDc4mJiWrQoIFOnjyppKQkJScnZzx34cIFJSUlqUiRIhmXD16/zFCSkpKS7irX9XWzrmvXrp22bt2qmJgYnThxQs2aNZMkffvtt6pRo4Z8fX1v+nkKFSqkt956S4ULF1b37t0zXkPx4sVVs2ZN7dq1K+O/TZs2acWKFZKu/b3ExcVl+lx/fHxdSEiIYmNjM22LjY3NVNgBAABYjbILAADkGq+//rqWLVumWbNmKSkpSU6nU/v27VPv3r1VqVIlde/eXeXKldMbb7yhCxcu6MKFCxo1apTuv/9+Va1aVffff7+8vb31+eefS5K2bdumHTt23PHx/fz8lJyc/KdnOz388MMqV66cxowZoxYtWsjf31/StbXAmjRp8qef38fHR1OnTlVCQkLG3RgjIiL0448/avXq1UpLS9OpU6fUu3dvTZo0SZL09NNP67PPPtOePXuUlpamZcuW6ccff7zp5+/QoYPmz5+vvXv3Kj09XevXr9fmzZvVpk2bO/47AAAAyGmUXQAAINeoUaOGPvnkE/3nP//RU089papVq+rll19WrVq19N5778nHx0fz5s1TWlqamjVrpgYNGig1NVUffPCBvL29VbRoUb322muaPXu2qlatqk8++SRj8fg70aBBA509e1bVqlXT+fPnb7lf27Zt9Z///CfjEsarV69qx44dql+//m2PUaxYMY0ZM0bLly/X+vXrFRISovfee09LlixR7dq11apVKz344IMZZVezZs3Uo0cPRUZGqnbt2tq+fbsqV64sHx+fGz733/72N3Xu3FkDBw5UWFiY5s2bp6lTp6pGjRp3/HcAAACQ02xOFlIAAAC4p2zatElvv/12xt0gc9L+/fuVL1++TOt2tW3bVp06ddLTTz+d48cHAADIbpzZBQAAcI9ISkrSvn37NGfOHD3zzDNuOeaOHTvUu3dvnT59Wk6nU+vWrdPhw4f12GOPueX4AAAA2c3b6gAAAAC45ueff1bfvn1Vu3ZtderUyS3HfO6553Ty5Em1adNGFy9e1IMPPqg5c+bc8o6MAAAA9zouYwQAAAAAAIAxuIwRAAAAAAAAxqDsAgAAAAAAgDEouwAAAAAAAGAMyi4AAAAAAAAYg7ILAAAAAAAAxqDsAgAAAAAAgDEouwAAAAAAAGAMyi4AAAAAAAAY4/8AamVx7GkO2vIAAAAASUVORK5CYII=
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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uK5du6aZM2eqePHiRsdDGiUnJ2vPnj26ePGiChYsqHLlynFbepN6++23tWXLFvn4+CgxMVHZsmWzr/HD5RbmcXdxzV69eqlGjRr27e+99562bt2qCxcucPq9iUyaNElLlixRjx49FBISkmL7N998oxs3bvAPZ8AJ3L1zdJ48eRQREaFq1app1qxZeuONN9S+fXuj4yGVevfura1bt3JWpQupXbu21q9fr6SkJNWqVUu//vqrJKlixYratWuXwemQFhEREfLw8FChQoUUGxurqKgolS1b1uhYToF/jaezokWLauXKldq4caOioqJUsGBB1apVi3dETOj8+fMqWLCgoqKiJElFihRRkSJFJEkxMTGSpMKFCxuWD2mzZcsWzZ07V7GxsZo7d64+/fRTff311zp48KDR0ZAK/fv319ixY7Vu3boU5dawYcP04Ycf6vvvvzcwHVKrR48eyp49uyIiIu7Zni1bNk2ePNmgZHCEf96N7e+4g625nDhxQnPmzNHZs2c1atQotW/fXoGBgfrggw8ot0yIsypdz5NPPqkJEyaoR48e8vX11ebNm5U1a1Z5eXkZHQ1pVKBAAW3evFlr1qxRy5YtOcHibzhzKwNdvXpVZ86c0ZNPPsknoQndvTtXQEDAPZfE2Gw2WSwW7gxkQnffuYqNjdXrr7+uVatW6datW6pTpw53v3QhcXFx8vHxMToGAOmeS2Hi4+N16tQpNWjQQJ999plBqZAWNWrU0JYtW+75vlm5cmXt2LHD4HQATp06pV69emnatGn6/fff1adPH1mtVg0YMIAC2oTOnDmjDh06KDExUVeuXNGiRYvUsGFDTZw40b5WaWZGw5JObt++rREjRihXrlzq37+/fvvtN3Xo0EFXr17V448/rtmzZ99zui+c28qVKyVJ69evNzgJHKlgwYKKiIhQ0aJFdenSJV2/fl1ubm66du2a0dGQSjExMZo/f76OHj2q69evK3v27CpVqpRCQkL02GOPGR0PqfTbb7/p+++/v2eeYWFhqlixotHx8Ahmz559z7alS5dShphQ8eLFNXfuXLVu3VrZsmXTkSNH5Onpybp4Jvbtt99q3rx5ioyMlJ+fn8LCwtSlSxdmalIlSpSw/xvG399fGzdu1LVr1+xrWsJcRo0apdDQUHXr1k2VKlVSsWLFNHLkSH3++eeUW5K4ZV86mTRpkvbv36+aNWtKunOr5EqVKmnPnj0KDg6233IX5lGoUCFJ0siRI+Xv73/PfwMHDjQ4IdKiUaNGevXVVxUdHa1atWqpW7du6tWrF9eum8ymTZtUr149HThwQEWLFtWzzz6rIkWK6LffflPjxo21ZcsWoyMiFRYsWKB27drJy8tLzZo10//+9z+FhobK29tb3bp105IlS4yOCAdr0qQJbx6ZUO/evTV+/HidOXNGHTt2VIsWLdSsWTM1bdrU6GhIg2+//VYzZ87U66+/ri+++ELt2rXTDz/8oOnTpxsdDam0a9eu+/73119/6eLFi6y3ZVL79+9Xp06dZLFY7IVzkyZN7lnGIbPizK10snr1ak2ePFklSpTQ5cuXtXfvXs2dO1fZs2dXx44d+aZvMmfPnrX/Y2rr1q33rBeSkJCgY8eOGZAMj6pz584qWrSocubMqXfffVdjx45VQkKC3n33XaOjIRXGjh2r0aNH66WXXrpn36pVqzRmzJgUa3HBuU2ZMkWTJk1SlSpV7tnXoEEDvffeeykWmof57dy5U9myZTM6BlIpKChIv/zyi7JkyaKWLVvqqaee0tWrV1WtWjWjoyENfvjhB02ePFllypSxbwsKClLPnj3VuXNnA5Mhtf7rTogsp2JOOXPm1MWLF1Os83zhwgXlzp3bwFTOg3IrnVy4cEElSpSQdOc2yVmyZNHTTz8tScqXL5+uXr1qZDykUuHChXXixAnFxsYqOTn5nksnvLy8uAWrSa1Zs0Z169a1r4M3fPhwgxMhLaKiolS/fv377qtfvz5lpclcunRJlSpVuu++ChUq6NKlSxmcCI4UHByc4hKnxMREXbx4Ud26dTMwFVLj7s11/ilfvnzKly+foqKiuMmOCcXExCggICDFtoCAAMXHxxsTCGl29OhRoyMgHTRq1Ehvvvmm3nrrLVmtVh08eFBjx47VK6+8YnQ0p0C5lU6yZMmiW7duycvLS3v27FHZsmWVJUsWSXd+IMiePbvBCZEabm5u9ktJhw4dqpEjRxqcCI4yatQoDRs2TE2aNFHz5s3tpTTMpUiRItq0aZOCg4Pv2bd27VoVLVrUgFRIq1KlSmnevHlq3br1Pfu+//57lS5d2oBUcJSePXum+NjNzU0lSpTgcnAT+WdBKf3/m+vcxVkh5vP4449r7dq1Kd4sWrt2rR5//HEDU+FR3bhxQ5cvX5bVapV05w2F48ePq27dugYnQ2p1795dN2/e1JtvvqkbN27ojTfeULNmzbjT8P/hbonp5M0331T58uUVEhKiVq1aqVWrVurUqZMk6fPPP9exY8c0adIkg1MiLa5cuaLhw4ere/fuKlGihCZMmKCzZ89q2LBhlJYmZLVatWXLFi1ZskQbNmzQU089pbCwML388stcImMimzdvVq9evVShQgWVLl1a2bJl040bN3Ty5Ent3LlTkyZN4jIZEzlw4IA6d+4sHx+fe+Z58eJFff311/azoeE6kpKSuJu0SURGRkq6cyOAPXv2qH///nrsscd07tw5jR07VoGBgerSpYvBKZFa69atU58+fVS3bl0VLVpUZ86c0fr161ms2sQWLlyoESNG6NatWym2+/r6cldwk7LZbEpOTtaVK1eUmJiofPnyyd3d3ehYToFyK52cPHlSbdq0UXx8vEqUKKH58+crW7ZsatGihY4fP645c+bwDqVJvfXWW7p8+bI+/vhj+fr66tSpUxo7dqx8fX01atQoo+PhEVy9elWrVq3S1KlTFR8fr7179xodCalw+vRpLVmyRCdPntS1a9fk7e2tUqVKqUmTJipevLjR8ZBKV65c0Zo1a1LMs3Tp0qpbt67y5MljdDw8gjNnzmjSpEmKjo5OcSbBn3/+qfDwcIPTITVq1qypZcuWpVjv5erVq2rQoIG2bdtmYDKkVXh4uBYvXqyLFy/K399fYWFhKleunNGxkEZ169bVa6+9puzZs2vXrl1q27atxo4dq2rVqul///uf0fGQSkePHlW3bt00YcIElStXTqNHj9a6des0ffp0ftYV5Va6SkhI0B9//KGAgAB5enpKksaPH68GDRrccz07zKNKlSpav359irO0EhISVLduXW3fvt3AZHgUERERWrp0qZYvX67r168rNDRUffv2NToWALicNm3ayGazycfHR5cuXVKZMmW0ZMkStWvXjksrTKZChQpau3atfHx87Nuio6PVqFEj7dy508BkACSpfPny2rdvnyIjI/X222/rhx9+UFRUlNq1a6eff/7Z6HhIpTZt2qhixYrq3r27PDw8lJSUpClTpmjv3r36+uuvjY5nOM79Tkc5cuS4552OPn36GBMGDmO1WpWcnJxim81m43RQk/rxxx+1ePFiHTx4UNWrV1f//v1Vu3Zt5mkyN2/e1CeffKLdu3er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FfXp00d79+7VK6+8olGjRkmSAgMD5efnp++//1758uUzOCUAAACcBeUWAAAwha1bt6pixYry8vIyOgoAAACcCOUWAAAAAAAATIs1twAAAAAAAGBalFsAAAAAAAAwLcotAAAAAAAAmBblFgAAQDo6ffq00REAAABcmofRAQAAANLTn3/+qSlTpmj79u26evWqfH191aBBA3Xr1k3Zs2dP12N/9913Wr16tWbPnp3m55g3b55OnDihdu3aqU6dOvL29pbFYpEkWa1WeXt7q0qVKho2bJjy5MnzyJk7deqkChUqqGvXro/8XAAAABmBM7cAAIDL2rt3r5o2bSp/f38tWbJE+/bt0/Tp03XgwAF16NBBycnJ6Xr82NjYR36On3/+WS+++KL94xUrVmjfvn3at2+fDhw4oNmzZ+vQoUMaNWrUIx9LkmbMmEGxBQAATIUztwAAgMt67733FBISol69etm3FStWTOPGjdN7772niIgIZcmSRWPHjtWOHTvk5uamKlWqaODAgcqfP7927NihN954Q8eOHbP//kGDBkmSPvroI33xxRc6ceKEPD09tWnTJmXLlk1NmjTRW2+9pcWLF2vq1KlKTk5WhQoVtHv3bgUHB6t69epav369/Pz8lDdvXvn7+2vEiBH25+/SpYvKlCmj3r176+rVqzp+/LgqVqyoc+fO3fc1lipVSnXr1tWWLVvs2w4fPqyPPvpIR48elY+Pj1599VW1bdvWfsbXrFmzNHPmTF2/fl1Vq1ZVUlKSSpcurZ49e6pNmzaqVKmSevbsKavVqhkzZmj+/PmKi4tTsWLF1Lt3b9WoUUOSFBwcrJYtW+qnn37SX3/9pccff1yDBg1SlSpVHDdEAACA/8CZWwAAwCWdOXNGJ06cUMOGDe/Zly9fPk2ePFn+/v7q0KGD3N3d9fPPP+unn36SJHXt2lVJSUkPdZyff/5Z1atX144dOzRixAhNnz5d+/fvV9OmTdWlSxd7sXXXwYMH9dNPP2nWrFkKCwvT6tWrdfv2bUnSxYsXtW3bNoWGhkqSNmzYoBo1asjd3f2+x7bZbDp06JBWr16tF154QZIUHR2ttm3bqkGDBvr11181efJkff/995o3b54kaeXKlZo4caI+/fRTbd26VRUqVNDPP/983+efNGmSvvvuO02YMEE7duxQhw4d1L17dx08eND+mIULF2rChAn69ddfFRAQoGHDhj3UnxsAAICjUG4BAACXdPeSwHz58j3wMbt371ZERISGDx+unDlzKleuXBo+fLiOHj2qQ4cOPdRxnnjiCYWEhMjd3V01a9aUn5/fvy4iX79+feXKlUu5cuXSiy++KDc3N23YsEGStHz5cgUGBqpo0aKSpLVr16pevXopfn/jxo1VoUIFPfvssypTpoyGDx+utm3bql+/fpKkZcuWqUSJEnrttdeUJUsWlSxZUh07dtR3330nSVqwYIFatmypoKAgZcmSRa+99pqeeeaZ+2ZduHChOnfurKeffloeHh56+eWXFRwcrAULFtgfExYWpscff1ze3t5q1KgRC+gDAIAMR7kFAABckp+fnyTpwoUL991/8eJFXbp0ST4+PsqRI4d9e44cOZQnTx5FRkam6jh3ZcmSRVar9YGPz58/v/3Xnp6eatiwoZYuXSpJWrx4sZo1ayZJunHjhvbt26eqVaum+P3Lli3T7t27tXHjRjVo0EBXr17VSy+9JA+PO6tNREZG6vDhw6pQoYL9v48//ljnz5+XJJ07d07+/v4pnvNumfZPFy9evGdfkSJFUvzZ/L089PDwkM1me+BrBwAASA+UWwAAwCX5+/urdOnSWrVq1T37Ll26pNq1aysyMlJxcXFKSEiw77t69ari4uLk5+dnvxzw7mWDkhQXF/dIue6ue3VXs2bNtGXLFu3bt09nz55V/fr1JUm//PKLKlWqJE9Pz/s+T968eTVmzBj5+vqqQ4cO9tdQsGBBVa5cWbt377b/t379ei1evFjSnT+XqKioFM/1z4/v8vf3V0RERIptERERKQo6AAAAo1FuAQAAl/Xuu+9q4cKFmjhxouLi4mSz2XTkyBF17dpVTz/9tDp06KCSJUvq/fff19WrV3X16lUNGzZMjz32mIKCgvTYY4/Jw8NDK1eulCT9+uuvCg8Pf+jje3l5KSEh4V/PZipTpoxKliypDz74QC+//LK8vb0l3VnLq27duv/6/FmyZNFnn32mixcv2u+W2KhRI+3fv1/Lli1TUlKSYmJi1LVrV3300UeSpBYtWmj+/Pk6ePCgkpKStHDhQu3fv/++z9+8eXNNmzZNhw8fVnJysn766Sdt2LBBTZs2feg/AwAAgPRGuQUAAFxWpUqVNGfOHP3+++965ZVXFBQUpF69eqlKlSqaMWOGsmTJoqlTpyopKUn169dX7dq1lZiYqJkzZ8rDw0P58+fXO++8o8mTJysoKEhz5syxL/b+MGrXrq34+Hg999xzunLlygMfFxoaqt9//91+SeLt27cVHh6umjVr/ucxChQooA8++ECLFi3STz/9JH9/f82YMUPz5s1T1apV1aRJExUvXtxebtWvX18dO3ZU9+7dVbVqVW3fvl1ly5ZVlixZ7nnu9u3b67XXXlPfvn1VoUIFTZ06VZ999pkqVar00H8GAAAA6c1iY2EEAAAAQ61fv16ffPKJ/W6N6eno0aPKmTNninW3QkND1apVK7Vo0SLdjw8AAOBonLkFAABgkLi4OB05ckRffvmlWrdunSHHDA8PV9euXXXhwgXZbDatWrVKJ0+e1PPPP58hxwcAAHA0D6MDAAAAZFaHDh3Sm2++qapVq6pVq1YZcszXX39dkZGRatq0qa5du6bixYvryy+/fOAdEwEAAJwdlyUCAAAAAADAtLgsEQAAAAAAAKZFuQUAAAAAAADTotwCAAAAAACAaVFuAQAAAAAAwLQotwAAAAAAAGBalFsAAAAAAAAwLcotAAAAAAAAmBblFgAAAAAAAEzr/wHoFMArr5csnAAAAABJRU5ErkJggg==
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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7NmzqFq1Kho0aAAAcHBwwIQJE/RbJRERUSWl8znq33//Hf369cONGzcAAGfOnEFAQAAOHz6s79qIiIgqPZ3fUYeFhWHFihWaw94jR46Eo6MjFixYAE9PT70XSEREVJnp/I7633//RceOHUXDOnTowC8/ISIiMgCdg7pu3bo4evSoaNjJkydRp04dvRVFREREBXQ+9B0YGIhx48ahe/fuqFu3Lu7du4eDBw/iq6++MkR9RERElZrOQe3n54datWph165d+Ouvv/DKK68gPDwcLVu2NER9RERElZrOQQ0Abm5ucHNz03ctREREVIjOQf3gwQOsXLkSN27cgEqlEt23YcMGvRVGREREZQjq6dOnIzExEV26dIGZmZkhaiIiIqKndA7qCxcuIDIyUvPd3kRERGQ4On88q2rVqjA3NzdELURERFSIzu+ox44di+nTp2P06NGwt7cX3cfPUhMREemXzkE9c+ZMAMDBgwcBADKZDIIgQCaT4fLly/qtjoiIqJLTOah///13Q9RBRERExSjTV4jWrVsXqamp+Ouvv1CzZk0oFArUrVvXEPURERFVajoHdVJSEgYPHoy33noLwcHBuH37Nrp164YzZ84Yoj4iIqJKTeegnjdvHpycnHDq1CnI5XI0aNAAgYGB+Prrrw1RHxERUaWmc1BHR0dj+vTpsLS0hEwmAwC8//77SEhI0HtxRERElZ3OQW1mZgalUgkAEAQBAJCRkQErKyv9VkZERES6B7WXlxemTp2KGzduQCaTISkpCV988QU8PT0NUR8REVGlpnNQT548GVWqVEGPHj3w5MkTdOjQAVlZWZgyZYoh6iMiIqrUdP4ctZWVFZYuXYrk5GTcuXMHDg4OqFWrliFqIyIiqvR0DupTp06Jbt+8eRM3b94EALRp00Y/VRERERGAMgT1sGHDigwzMTHBK6+8wm8tIyIi0jOdg/rKlSui28nJyVi+fDm/mYyIiMgAdL6YrDA7OztMnToV33//vT7qAQA8fvwY06ZNg5ubG9q0aYOxY8fi4cOHAIBz584hICAArq6u8PLywrZt2/S2XCIiIql54aAGgNTUVGRnZ+tjVgCAjz76CJmZmTh48CAOHToEU1NTfPbZZ0hNTUVgYCD69euHU6dOISQkBKGhoTh//rzelk1ERCQlOh/6nj59uuh2bm4u4uLi0K5dO70UdPHiRZw7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
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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U6caTz/9tFG3bl2jffv2xq5duxwZHdnsf38O8HtlwWIxDK5dAQAAAACYg8tlAQAAAACmoWQCAAAAAExDyQQAAAAAmIaSCQAAAAAwDSUTAAAAAGAaSiYAAAAAwDSUTAAAAADIpy5fvqwWLVooNjY2y+ts3rxZrVq1kr+/v1q0aKFVq1bZtU9KJgAAuczNmzd17ty5LC176tSp7A2TTfJqbgDIS7799lt16tRJcXFxWV5n//79GjZsmN544w0dPnxY48aN05gxY/T9999neRuUTAAAcpkuXbpo3759913uxx9/VKtWrbK83ZCQEEVHRz9QpujoaIWEhDzQuv9r8eLFGjlypCm5AAB3t3r1ar3++usaPHjwHfP27dunyMhIBQYGKjw8XDExMbZ5CxYs0IsvvqgmTZrIYrGofv36+uKLL1SxYsUs75uSCQBALpOYmJil5ZKSkpSWlpbNacx3+fJlR0cAgHzvySef1NatW/Xss89mmn7s2DENGDBAffv2VWxsrMaNG6f33ntPu3fvliR9//338vT0VN++fRUcHKy2bdsqLi5Onp6eWd43JRMAgFykV69eOnv2rKKiojR27FgdOnRIL7zwggIDAxUSEqJ//vOfSk1N1ZkzZ9SnTx9JUkBAgA4fPqzk5GSNGDFCoaGh8vf3V+PGjTVr1qwHynHixAl169ZNAQEBat26tX788cdM83/44Qd169ZN9erVU2hoqBYsWCDDMCRJqampmjRpklq2bKmAgAA1aNBA48aNk2EYWr16tWbPnq1Dhw4pMDAw0/Y6d+6sunXrKjw8XAcOHLDNmzZtmpo0aaKgoCB16NBB27Zte6BjAoCCxNvbWy4uLndMX7ZsmZo1a6bQ0FA5Ozurbt266tixoxYvXixJunr1qubNm6cBAwZo7969+sc//qHBgwfr3//+d5b3fedeAQCAw8yfP18hISEaOHCg/P391bZtW73++uv69NNP9fvvv+uVV16xlck5c+boxRdf1OHDhyVJo0eP1m+//aZVq1apWLFi2rJli1599VW1bNlSlSpVynKGtLQ09evXT0899ZTmzp2ruLg49enTR05Of/5t+vz58+revbsGDx6s+fPn6/Tp03r55Zfl4eGhzp07a+HChdq9e7cWLlyoMmXK6PDhw+ratauaN2+u9u3b67ffftOBAwf02Wef2fa5Z88ezZkzR+XLl9fo0aM1cuRIbd68Wfv379fy5csVHR0tb29vLV++XMOHD9dTTz0lV1dXc998ACgA4uPjtX///kx/6MvIyLBdDuvm5qYOHTooICBAkhQaGqoGDRpo8+bNqlOnTpb2wZlMAAByqXXr1snPz0/du3eXm5ubKlWqpKFDh2rlypWyWq13LP/KK6/on//8p4oWLapz587J3d1dknThwgW79nv48GH9/vvvevPNN+Xu7q6qVauqZ8+etvkxMTGqUqWKXnjhBbm6uurRRx9V7969bX8F79ixoxYsWCBvb29duHBBKSkpKlKkiM6fP/+X++zUqZMqVqwoFxcXPfPMMzpz5owkyd3dXVevXtWKFSv0448/6rnnntM333xDwQSAB+Tj46P27dvr0KFDtv82b96sTz75RJJUpUoVpaamZlonIyPDdrVKVnAmEwCAXCohIUEVKlTINO2hhx5SSkqKEhIS7rr8u+++qx9//FEPPfSQHnvsMUm6ayG9l/Pnz6tkyZLy8PCwTbv9gQ/x8fH64YcfMv0V3Gq1ytnZWZJ048YNjR07VgcPHpSPj49q1qwpwzDumeP2e31cXV2VkZEh6c9LgadNm6bPPvtMc+fOlYeHh7p166YBAwbYzqwCALIuMjJSPXv2VGhoqBo2bKi4uDj17dtXTz/9tN5++209//zzGjdunBo3bqz69etr69atio2N1ZAhQ7K8D0omAAC5lK+vr7Zs2ZJpWlxcnNzc3FSiRIk7lh80aJBCQkI0b948ubi4KDExUStWrLB7v+XKldPly5d17do1FSlSRJIyfaSKj4+PgoODNW/ePNu0xMREXbt2TZI0YsQIlShRQnv27JG7u7usVqvq1atndw5JOnv2rEqXLq158+YpNTVV33zzjQYOHKhatWqpadOmD7RNACjI6tSpoylTpmjKlCkaNGiQChUqpFatWtlKZIcOHeTk5KQJEybot99+k6+vrz766CPVqlUry/vgT4AAAOQybm5uSkpKUnh4uE6cOKGFCxcqNTVVcXFxmjJlilq3bi03Nzfb5bBJSUm2/3t4eMjZ2VmXL1/W+PHjJcnuJ9AGBATo4Ycf1vjx43Xjxg2dPn1a8+fPt81v3bq1jhw5opiYGKWnp+vChQvq37+/Jk6cKElKTk6Wu7u7nJyclJycrMmTJys5OdmWw93dXcnJyVm69Oo///mPXnrpJR07dkxubm4qXbq0JKlkyZJ2HRMAFGQ///yzgoODba+bNm2q6Ohoffvtt9qzZ4+GDRsmNzc32/z27dtr3bp1Onz4sNavX68WLVrYtT9KJgAAuUxkZKQ++ugj/fOf/9TcuXO1efNmNWzYUF26dFGjRo00atQoSVK1atX0xBNPqHHjxtq5c6cmTJigjRs3qm7duoqIiFDZsmVVs2ZNHT9+3K79Ozs765NPPtGFCxfUsGFDvfTSS2rWrJltvq+vr+bOnavly5erYcOGatu2rR555BFbyRwxYoSOHTumoKAgPfPMM0pOTlbjxo1tOZ5++mlduXJFTzzxhP744497ZgkLC1OvXr00YMAA+fv7a9CgQXrnnXey/PAJAEDOsxj23MEJAAAAAMA9cCYTAAAAAGAaHvwDAEABExERoZMnT/7l/Dlz5mR6ciwAAPbgclkAAAAAgGm4XBYAAAAAYBpKJgAAAADANJRMAAAAAIBpKJkAAAAAANNQMgEAAAAApqFkAgAAAABMQ8kEAAAAAJiGkgkAAAAAMM3/AZ2f+Q6aHeVhAAAAAElFTkSuQmCC
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot: xlabel=&#39;date&#39;, ylabel=&#39;date&#39;&gt;</pre>
</div>

</div>
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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
"
class="
"
>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h1 id="lets-just-look-at-the-US-data">lets just look at the US data<a class="anchor-link" href="#lets-just-look-at-the-US-data">&#182;</a></h1><h3 id="Questions-to-explore:">Questions to explore:<a class="anchor-link" href="#Questions-to-explore:">&#182;</a></h3><ul>
<li>What is the total number of deaths from covid in the US?</li>
<li>What is the Distribution of the daily death counts?</li>
<li>What is the mean and standard deviation of number of daily deaths from covid in the US?</li>
<li>What is the trend in deaths in the US from covid like over the duration of the pandemic?</li>
</ul>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;seaborn.axisgrid.FacetGrid at 0x162589e70&gt;</pre>
</div>

</div>
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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
"
class="
"
>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>1115564</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>1000.5058295964126</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>931.1271092807036</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">

<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>daily_deaths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1115</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>851</td>
    </tr>
    <tr>
      <th>top</th>
      <td>0</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>34</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child jp-OutputArea-executeResult">


<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>427.41</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>--The distribution of daily deaths in the US is right skewed.<br />
Lets check the trend in the US Covid death rate by plotting number of deaths over time</p>

</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell  jp-mod-noInput ">

<div class="jp-Cell-outputWrapper">
<div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
</div>

<div class="jp-OutputArea jp-Cell-outputArea">
<div class="jp-OutputArea-child">


<div class="jp-RenderedImage jp-OutputArea-output ">
"
class="
"
>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell jp-MarkdownCell jp-Notebook-cell">
<div class="jp-Cell-inputWrapper">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea"><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h1 id="Time-Series-Analysis">Time Series Analysis<a class="anchor-link" href="#Time-Series-Analysis">&#182;</a></h1>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs jp-mod-noInput ">

</div>
</body>







</html>


[Top of Page](#page-top)