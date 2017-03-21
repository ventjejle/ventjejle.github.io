---
layout: default
title:  "Dimensionality Reduction"
date:   2016-11-18 11:00:49 +0700
categories: machine learning
---
<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />
<title>Dimensionality Reduction</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>

<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.6 (http://getbootstrap.com)
 * Copyright 2011-2015 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    color: #000 !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.2.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.2.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.2.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.2.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.2.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.2.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=1);
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2);
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1);
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1);
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
@media (max-width: 991px) {
  #ipython_notebook {
    margin-left: 10px;
  }
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#login_widget {
  float: right;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  text-align: center;
  vertical-align: middle;
  display: inline;
  opacity: 0;
  z-index: 2;
  width: 12ex;
  margin-right: -12ex;
}
.alternate_upload .btn-upload {
  height: 22px;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: baseline;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI colors. */
.ansibold {
  font-weight: bold;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  border-left-width: 1px;
  padding-left: 5px;
  background: linear-gradient(to right, transparent -40px, transparent 1px, transparent 1px, transparent 100%);
}
div.cell.jupyter-soft-selected {
  border-left-color: #90CAF9;
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected {
  border-color: #ababab;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 5px, transparent 5px, transparent 100%);
}
@media print {
  div.cell.selected {
    border-color: transparent;
  }
}
div.cell.selected.jupyter-soft-selected {
  border-left-width: 0;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 7px, #E3F2FD 7px, #E3F2FD 100%);
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #66BB6A -40px, #66BB6A 5px, transparent 5px, transparent 100%);
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
@-moz-document url-prefix() {
  div.inner_cell {
    overflow-x: hidden;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  padding: 0.4em;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. We need the 0 value because of how we size */
  /* .CodeMirror-lines */
  padding: 0;
  border: 0;
  border-radius: 0;
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul {
  list-style: disc;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ul ul {
  list-style: square;
  margin: 0em 2em;
}
.rendered_html ul ul ul {
  list-style: circle;
  margin: 0em 2em;
}
.rendered_html ol {
  list-style: decimal;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
  margin: 0em 2em;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  background-color: #fff;
  color: #000;
  font-size: 100%;
  padding: 0px;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: 1px solid black;
  border-collapse: collapse;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  border: 1px solid black;
  border-collapse: collapse;
  margin: 1em 2em;
}
.rendered_html td,
.rendered_html th {
  text-align: left;
  vertical-align: middle;
  padding: 4px;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget {
  float: right !important;
  float: right;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 20ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  margin-top: 6px;
}
span.save_widget span.filename {
  height: 1em;
  line-height: 1em;
  padding: 3px;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  display: none;
}
.command-shortcut:before {
  content: "(command)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    
/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}

@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Pendahuluan">Pendahuluan<a class="anchor-link" href="#Pendahuluan">&#182;</a></h1><p>Ketika kita akan melakukan analisis data, entah itu prediksi atau klasifikasi, kita membutuhkan data yang cukup banyak. Hal itu untuk akan membantu kita untuk memenuhi signifikan statistik untuk pengujian hipotesis kita nantinya. Makin banyak data makin baik, walau ketika belajar Confidence Level dan Interval ternyata pengujian terhadap sampel random lebih baik <a href="https://www.qualtrics.com/blog/determining-sample-size/">sekitar 10% dari populasi</a>.</p>
<p>Misalnya, kita sudah menentukan populasi, Confidence Level, dan Confidence Interval, maka kita bisa menentukan sampel dan melakukan pengambilan data. Ternyata data yang kita dapat memiliki banyak fitur atau dimensi. Contohnya data di bawah ini:
<img src="http://thumbnails116.imagebam.com/51544/a7aa47515437701.jpg" alt="Human Development Index based on GDP"><br>
Kesusahan akan terjadi ketika kita akan melakukan analisis terhadap data di atas. Jumlah fitur atau dimensinya cukup banyak, yaitu 12. Untuk melakukan prediksi atau klasifikasi terhadap data dengan lebh dari 3 dimensi saja sudah lumayan memakan waktu dan biaya komputasi, apalagi dengan 12 dimensi.</p>
<p><em>Dimensionality reduction</em> adalah konsep untuk menemukan pola dalam sehingga kita bisa melakukan pengurangan (reduksi) terhadap jumlah dimensi dengan tetap mempertahankan informasi relevan yang ada dalam data. Keluaran yang diinginkan adalah kita mentransformasikan data berdimensi <em>n</em> menjadi data berdimensi <em>k</em>. Tujuan kita melakukan dimensionality reduction, adalah: (a) menurunkan biaya komputasi yang dibutuhkan ketika melakukan inferensi lanjutan; (b) mempermudah ketika akan melakukan visualisasi data, tentu lebih mudah melakukan visualisasi data berdimensi 3 ke bawah.</p>
<h1 id="Principal-Component-Analysis-(PCA)">Principal Component Analysis (PCA)<a class="anchor-link" href="#Principal-Component-Analysis-(PCA)">&#182;</a></h1><p>Principal Component Analysis atau PCA merupakan <a href="https://www.analyticsvidhya.com/blog/2015/07/dimension-reduction-methods/">salah satu metode</a> yang digunakan dalam <em>dimensionality reduction</em>. PCA berusaha melakukan proyeksi keseluruhan data (tanpa label) ke subspace yang berbeda dimensi. Misal, kita memiliki data berdimensi 3, PCA akan memproyeksikan semua data tersebut ke sebuah permukaan yang bisa digambar ke dalam diagram cartesius berdimensi 2.</p>
<h2 id="Algoritma-PCA">Algoritma PCA<a class="anchor-link" href="#Algoritma-PCA">&#182;</a></h2><ol>
<li><a href="#get-data">Mendapatkan data: x(1), x(2), … x(m)</a></li>
<li><a href="#prapemrosesan">Prapemrosesan data: kuantifikasi, normalisasi and <em>feature scaling</em></a></li>
<li><a href="#covariance">Menghitung matriks covariance C</a></li>
<li><a href="#eigenvector">Menghitung eigenvector dan eigenvalues matriks C</a></li>
<li><a href="#eigenvalue">Memilih sejumlah <em>k</em> eigenvector</a></li>
<li><a href="#final">Mendapatkan matriks proyeksi</a></li>
</ol>
<h1 id="Implementasi-PCA-dengan-Python">Implementasi PCA dengan Python<a class="anchor-link" href="#Implementasi-PCA-dengan-Python">&#182;</a></h1><p>Kita akan menunjukkan contoh melakukan PCA dengan Python dan data Human Development Report berdasarkan GDP. Sebenarnya data Human Development dari UNDP memiliki banyak sheet, namun kita akan mengambil satu sheet saja. File excel Human Development Report tahun 2014 dari UNDP bisa diunduh di <a href="http://hdr.undp.org/sites/default/files/hdr14_statisticaltables.xls">link ini</a>.
<a name="get-data"></a></p>
<h2 id="Mendapatkan-Data">Mendapatkan Data<a class="anchor-link" href="#Mendapatkan-Data">&#182;</a></h2><p>Kita sudah membersihkan data sheet yang digunakan. Excel yang digunakan dalam PCA kali ini bisa diunduh di <a href="https://mega.nz/#!fJM0lTDI!YHrQM8JphLPdjHhsgil2kg-RoKIn3xboC2Tvd7XIfIM">sini</a>.
Pertama kita akan mengimport package python yang digunakan dan akan melakukan pembacaan data excel dan mengubanya menjadi struktur matriks. Label negara maupun nama variabel tidak kita masukkan.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">openpyxl</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="c1"># Membaca excel</span>
<span class="n">excel</span> <span class="o">=</span> <span class="n">openpyxl</span><span class="o">.</span><span class="n">load_workbook</span><span class="p">(</span><span class="s1">&#39;HDI_from_GDP.xlsx&#39;</span><span class="p">)</span>
<span class="n">sheet</span> <span class="o">=</span> <span class="n">excel</span><span class="o">.</span><span class="n">get_sheet_by_name</span><span class="p">(</span><span class="s1">&#39;Sheet1&#39;</span><span class="p">)</span>

<span class="c1"># Mengambil setiap nilai cell dalam excel dan menyimpannya menjadi array</span>
<span class="n">_matrix</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">14</span><span class="p">,</span><span class="mi">12</span><span class="p">))</span>
<span class="k">for</span> <span class="n">rowNum</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">4</span><span class="p">,</span><span class="n">sheet</span><span class="o">.</span><span class="n">max_row</span><span class="o">+</span><span class="mi">1</span><span class="p">):</span>
    <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span><span class="n">sheet</span><span class="o">.</span><span class="n">max_column</span><span class="p">):</span>
        <span class="c1">#_row.append(sheet.cell(row=rowNum,column=col).value)</span>
        <span class="n">_matrix</span><span class="p">[</span><span class="n">rowNum</span><span class="o">-</span><span class="mi">4</span><span class="p">,</span><span class="n">col</span><span class="o">-</span><span class="mi">3</span><span class="p">]</span><span class="o">=</span> <span class="n">sheet</span><span class="o">.</span><span class="n">cell</span><span class="p">(</span><span class="n">row</span><span class="o">=</span><span class="n">rowNum</span><span class="p">,</span> <span class="n">column</span><span class="o">=</span><span class="n">col</span><span class="p">)</span><span class="o">.</span><span class="n">value</span>

<span class="nb">print</span><span class="p">(</span><span class="n">_matrix</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>[[  3.15457507e+02   6.28580090e+04   2.05729366e+01   2.13114427e+01
    1.80451566e+00   3.29530689e+01   1.69491000e+00   1.15605023e+00
    8.69562223e+01   1.14159484e+02   1.15000000e+00   6.80000000e+00]
 [  9.60647458e+02   4.22782967e+04   2.78527873e+01   1.79319801e+01
    3.40796465e+00   6.36466130e+01   2.37364000e+00   2.39385620e+00
    1.54355462e+02   1.21814980e+02   1.16000000e+00   1.27000000e+01]
 [  4.10179738e+02   5.12925932e+04   2.04037006e+01   1.11175230e+01
    1.96672903e+00   2.41758012e+01   2.99067000e+00   7.31279544e-01
    1.92629870e+02   1.04030456e+02   1.05000000e+00   9.20000000e+00]
 [  7.11291376e+02   4.24525807e+04   1.68375960e+01   2.84036308e+01
    7.32791100e-03   2.51958989e+01   1.83017000e+00   1.68612939e+00
    2.16042608e+02   1.13215978e+02   8.90000000e-01   4.20000000e+00]
 [  1.59654779e+04   5.08593942e+04   1.46911876e+01   1.73060375e+01
   -2.64451525e+00   5.48883281e+01   2.89662000e+00   1.09164206e+00
    2.31568654e+02   1.17564626e+02   1.00000000e+00   9.60000000e+00]
 [  3.37518347e+03   4.19664150e+04   1.75686408e+01   1.94830194e+01
    1.16372751e+00   1.54001760e+01   2.81856000e+00   8.91196425e-01
    1.23578701e+02   1.12619434e+02   1.10000000e+00   1.38000000e+01]
 [  1.43456145e+02   3.23602322e+04   1.88140001e+01   2.01466399e+01
    3.09915826e-01   4.57840142e+01   1.30137000e+00   6.27506205e+00
    1.57782784e+02   1.21079260e+02   1.27000000e+00   1.30000000e+01]
 [  1.41060958e+03   4.05880449e+04   2.20124761e+01   2.08850399e+01
    7.88332396e-01   5.32734223e+01   1.79871000e+00   1.53506124e+00
    1.77647882e+02   1.13741528e+02   1.28000000e+00   9.40000000e+00]
 [  3.79703196e+02   7.14748882e+04   2.41257320e+01   9.65689076e+00
   -3.55357754e+00   3.43646645e+01   2.42770000e+00   3.42033940e-02
    9.95232962e+01   1.25002305e+02   1.29000000e+00   1.58000000e+01]
 [  2.32186334e+02   4.15243394e+04   1.76228830e+01   2.85735947e+01
    1.68006081e-01   3.88890802e+01   3.05949000e+00   1.45183514e+00
    2.06582458e+02   1.16889695e+02   1.13000000e+00   2.09000000e+01]
 [  1.96863235e+02   4.29186082e+04   1.00473734e+01   1.75674592e+01
   -3.38426053e+00   3.60054588e+01   1.79259000e+00   1.59098034e+00
    2.02107099e+02   1.11954387e+02   9.90000000e-01   4.20000000e+00]
 [  3.98287537e+02   4.18396774e+04   1.87706122e+01   2.68531176e+01
    7.35463344e-01   1.12216127e+01   3.39902000e+00   1.56627767e+00
    1.44792798e+02   1.12049059e+02   1.14000000e+00   1.00000000e+01]
 [  1.23646576e+01   3.85532921e+04   1.43873592e+01   2.55144316e+01
   -2.27456450e-01   2.85020073e+01   2.64312000e+00   7.81524016e+00
    1.43164618e+02   1.63076923e+02   1.13000000e+00   3.92000000e+01]
 [  2.20697434e+03   3.46939107e+04   1.41578952e+01   2.20923602e+01
    2.19883647e+00   3.55924447e+01   1.76231000e+00   6.52471437e-01
    2.10105519e+02   1.22993583e+02   1.20000000e+00   2.29000000e+01]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kita mendapatkan matriks seperti di atas. Mencetak matriks dari numpy memang tampilannya kurang jelas dan seringkali membingungkan. Untuk keperluan visualisasi saja, kita akan mengkonversi matriks numpy menjadi dataframe panda agar tampilan matriksnya lebih jelas dan mudah dibaca.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[69]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">_matrix</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>              0            1          2          3         4          5   \
0     315.457507  62858.00895  20.572937  21.311443  1.804516  32.953069   
1     960.647458  42278.29673  27.852787  17.931980  3.407965  63.646613   
2     410.179738  51292.59315  20.403701  11.117523  1.966729  24.175801   
3     711.291376  42452.58065  16.837596  28.403631  0.007328  25.195899   
4   15965.477910  50859.39421  14.691188  17.306037 -2.644515  54.888328   
5    3375.183468  41966.41504  17.568641  19.483019  1.163728  15.400176   
6     143.456145  32360.23219  18.814000  20.146640  0.309916  45.784014   
7    1410.609577  40588.04493  22.012476  20.885040  0.788332  53.273422   
8     379.703196  71474.88818  24.125732   9.656891 -3.553578  34.364665   
9     232.186334  41524.33942  17.622883  28.573595  0.168006  38.889080   
10    196.863235  42918.60825  10.047373  17.567459 -3.384261  36.005459   
11    398.287537  41839.67738  18.770612  26.853118  0.735463  11.221613   
12     12.364658  38553.29206  14.387359  25.514432 -0.227456  28.502007   
13   2206.974337  34693.91067  14.157895  22.092360  2.198836  35.592445   

         6         7           8           9     10    11  
0   1.69491  1.156050   86.956222  114.159484  1.15   6.8  
1   2.37364  2.393856  154.355462  121.814980  1.16  12.7  
2   2.99067  0.731280  192.629870  104.030456  1.05   9.2  
3   1.83017  1.686129  216.042608  113.215978  0.89   4.2  
4   2.89662  1.091642  231.568654  117.564626  1.00   9.6  
5   2.81856  0.891196  123.578701  112.619434  1.10  13.8  
6   1.30137  6.275062  157.782784  121.079260  1.27  13.0  
7   1.79871  1.535061  177.647882  113.741528  1.28   9.4  
8   2.42770  0.034203   99.523296  125.002305  1.29  15.8  
9   3.05949  1.451835  206.582458  116.889695  1.13  20.9  
10  1.79259  1.590980  202.107099  111.954387  0.99   4.2  
11  3.39902  1.566278  144.792798  112.049059  1.14  10.0  
12  2.64312  7.815240  143.164618  163.076923  1.13  39.2  
13  1.76231  0.652471  210.105519  122.993583  1.20  22.9  
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kini isi matriks tercetak dengan lebih jelas. Bisa kita perhatikan bahwa matriks ini adalah matriks 14x12, terdiri dari 14 baris (sesuai dengan banyak negara) dan 12 kolom (sesuai dengan banyak variabel). Dataframe df ini tidak akan kita gunakan untuk langkah selanjutnya, lebih mudah menghitung covariance dan eigenvector dengan numpy. Dataframe akan digunakan untuk tujuan mencetak isi matriks saja.
<a name="prapemrosesan"></a></p>
<h2 id="Prapemrosesan-Data">Prapemrosesan Data<a class="anchor-link" href="#Prapemrosesan-Data">&#182;</a></h2><p>Setelah mendapatkan representasi data dalam matriks, sekarang saatnya untuk melakukan normalisasi dan <em>feature scaling</em>. Kalau kita perhatikan di keluaran matriks di atas, nilai satu data dengan data lain memiliki perbedaan yang cukup jauh karena itu kita perlu melakukan normalisasi. Langkah ini adalah langkah yang sangat penting, karena bila kita tidak melakukan normalisasi akan berakibat pada hilangnya informasi dalam data. Padahal kita berusaha menjadi informasi yang ada tetap relevan atau minimal hilangnya.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[76]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Kita membuat matriks baru, yaitu matriks normalisasi</span>
<span class="n">matrixNorm</span> <span class="o">=</span> <span class="p">(</span><span class="n">_matrix</span> <span class="o">-</span> <span class="n">_matrix</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span> <span class="o">/</span> <span class="n">_matrix</span><span class="o">.</span><span class="n">std</span><span class="p">()</span>
<span class="c1">#print(matrixNorm)</span>
<span class="n">dfn</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">matrixNorm</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">dfn</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>          0         1         2         3         4         5         6   \
0  -0.283671  4.565030 -0.306532 -0.306475 -0.307987 -0.305572 -0.307996   
1  -0.233652  2.969558 -0.305968 -0.306737 -0.307863 -0.303193 -0.307943   
2  -0.276327  3.668404 -0.306545 -0.307265 -0.307975 -0.306253 -0.307895   
3  -0.252983  2.983070 -0.306822 -0.305925 -0.308127 -0.306174 -0.307985   
4   0.929619  3.634820 -0.306988 -0.306785 -0.308332 -0.303872 -0.307903   
5  -0.046461  2.945379 -0.306765 -0.306617 -0.308037 -0.306933 -0.307909   
6  -0.297006  2.200646 -0.306669 -0.306565 -0.308103 -0.304578 -0.308026   
7  -0.198768  2.838519 -0.306421 -0.306508 -0.308066 -0.303997 -0.307988   
8  -0.278690  5.233066 -0.306257 -0.307378 -0.308403 -0.305463 -0.307939   
9  -0.290127  2.911107 -0.306761 -0.305912 -0.308114 -0.305112 -0.307890   
10 -0.292865  3.019199 -0.307348 -0.306765 -0.308390 -0.305336 -0.307988   
11 -0.277249  2.935554 -0.306672 -0.306045 -0.308070 -0.307257 -0.307864   
12 -0.307169  2.680772 -0.307012 -0.306149 -0.308145 -0.305918 -0.307922   
13 -0.137028  2.381568 -0.307030 -0.306414 -0.307957 -0.305368 -0.307991   

          7         8         9         10        11  
0  -0.308038 -0.301386 -0.299277 -0.308038 -0.307600  
1  -0.307942 -0.296161 -0.298683 -0.308037 -0.307143  
2  -0.308070 -0.293193 -0.300062 -0.308046 -0.307414  
3  -0.307996 -0.291378 -0.299350 -0.308058 -0.307802  
4  -0.308043 -0.290174 -0.299013 -0.308050 -0.307383  
5  -0.308058 -0.298547 -0.299396 -0.308042 -0.307057  
6  -0.307641 -0.295895 -0.298740 -0.308029 -0.307119  
7  -0.308008 -0.294355 -0.299309 -0.308028 -0.307398  
8  -0.308125 -0.300411 -0.298436 -0.308027 -0.306902  
9  -0.308015 -0.292112 -0.299065 -0.308040 -0.306507  
10 -0.308004 -0.292459 -0.299448 -0.308050 -0.307802  
11 -0.308006 -0.296902 -0.299440 -0.308039 -0.307352  
12 -0.307521 -0.297028 -0.295484 -0.308040 -0.305088  
13 -0.308077 -0.291838 -0.298592 -0.308034 -0.306352  
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a name="covariance"></a></p>
<h2 id="Menghitung-Matriks-Covariance">Menghitung Matriks Covariance<a class="anchor-link" href="#Menghitung-Matriks-Covariance">&#182;</a></h2><p>PCA menggunakan aljabar linier, tepatnya operasi matriks, untuk melakukan proyeksi. Dengan menggunakan operasi matriks tersebut, PCA berusaha menjaga informasi relevan tetap ada, walau akan mereduksi jumlah fitur. Matriks covariance adalah matriks yang menunjukkan besarnya hubungan antara variabel dalam matriks asal. Anggap kita punya 2 vektor X(x1, x2) dan Y(y1, y2). Maka ada 4 covariance yang harus diukur: x1 dengan y1, x1 dengan y2, x2 dengan y1 , dan x2 dengan y2.<br>
Rumus covariance:<br>
<img src="http://resources.esri.com/help/9.3/ArcGISEngine/java/gp_toolref/spatial_analyst_tools/sa_multivar_bandcollectionstats_frmla_1.gif" alt="Rumus Covariance"><br>
Perlu diperhatikan bila kita memiliki <em>n</em> dimensi, maka hasil dari covariance adalah matriks berukuran <em>nxn</em>. Kita sedang menganalisis data dengan 12 dimensi, sehingga matriks covariance kita adalah 12x12. Kita akan menggunakan numpy untuk menghitung matriks covariance sehingga tidak perlu menghitung satu-satu nilai covariance.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[79]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">covarianceMatrix</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">cov</span><span class="p">(</span><span class="n">matrixNorm</span><span class="o">.</span><span class="n">T</span><span class="p">)</span>
<span class="n">dfcov</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">covarianceMatrix</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Covariance matrix </span><span class="se">\n</span><span class="si">%s</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">dfcov</span>)
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>Covariance matrix 
              0             1             2             3             4   \
0   1.036876e-01  2.450832e-02 -2.626427e-05 -2.347956e-05 -1.597201e-05   
1   2.450832e-02  6.786945e-01  1.059987e-04 -2.072808e-04 -4.778791e-05   
2  -2.626427e-05  1.059987e-04  1.227886e-07 -4.998165e-08  2.379984e-08   
3  -2.347956e-05 -2.072808e-04 -4.998165e-08  1.981826e-07  1.786986e-08   
4  -1.597201e-05 -4.778791e-05  2.379984e-08  1.786986e-08  2.626246e-08   
5   1.238566e-04 -5.737301e-05  1.259787e-07 -1.103952e-07 -1.026039e-09   
6   3.934709e-06  5.875836e-06  1.068221e-09  4.353130e-10 -1.578062e-10   
7  -1.137838e-05 -6.895307e-05 -9.704455e-09  2.423733e-08  1.338211e-09   
8   4.464385e-04 -1.387071e-03 -5.979899e-07  3.311973e-07 -6.599780e-08   
9  -2.850565e-05 -1.339980e-04 -5.269599e-08  9.880123e-08 -1.885051e-08   
10 -8.532318e-07  4.955890e-07  1.591190e-09 -8.797615e-10  2.422975e-10   
11 -2.916951e-05 -1.471380e-04 -3.525792e-08  7.301162e-08  9.338333e-09   

              5             6             7             8             9   \
0   1.238566e-04  3.934709e-06 -1.137838e-05  4.464385e-04 -2.850565e-05   
1  -5.737301e-05  5.875836e-06 -6.895307e-05 -1.387071e-03 -1.339980e-04   
2   1.259787e-07  1.068221e-09 -9.704455e-09 -5.979899e-07 -5.269599e-08   
3  -1.103952e-07  4.353130e-10  2.423733e-08  3.311973e-07  9.880123e-08   
4  -1.026039e-09 -1.578062e-10  1.338211e-09 -6.599780e-08 -1.885051e-08   
5   1.334089e-06 -2.056638e-08  1.891450e-08  1.020881e-06  8.844530e-08   
6  -2.056638e-08  2.488861e-09 -1.662301e-09  4.408013e-09 -8.837827e-11   
7   1.891450e-08 -1.662301e-09  2.922938e-08 -6.066858e-08  1.348368e-07   
8   1.020881e-06  4.408013e-09 -6.066858e-08  1.208911e-05 -7.715825e-07   
9   8.844530e-08 -8.837827e-11  1.348368e-07 -7.715825e-07  1.137134e-06   
10  2.718619e-09 -8.969393e-11  2.304470e-10 -1.640179e-08  2.137132e-09   
11 -4.502393e-08  7.496609e-09  6.937493e-08 -2.977094e-07  6.611814e-07   

              10            11  
0  -8.532318e-07 -2.916951e-05  
1   4.955890e-07 -1.471380e-04  
2   1.591190e-09 -3.525792e-08  
3  -8.797615e-10  7.301162e-08  
4   2.422975e-10  9.338333e-09  
5   2.718619e-09 -4.502393e-08  
6  -8.969393e-11  7.496609e-09  
7   2.304470e-10  6.937493e-08  
8  -1.640179e-08 -2.977094e-07  
9   2.137132e-09  6.611814e-07  
10  8.104061e-11  2.095167e-09  
11  2.095167e-09  5.039395e-07  

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a name="eigenvector"></a></p>
<h2 id="Menghitung-Eigenvector-dan-Eigenvalue">Menghitung Eigenvector dan Eigenvalue<a class="anchor-link" href="#Menghitung-Eigenvector-dan-Eigenvalue">&#182;</a></h2><p>Setelah mendapatkan matriks covariance, kita mendapatkan hubungan dari masing-masing variabel yang ada. Namun, kita tidak tahu bagaimana membagi hubungan yang ada. Maksudnya, bila variabel 1 memiliki hubungan yang kuat terhadap variabel 2, belum tentu variabel 1 memiliki hubungan yang sama dengan variabel 3. Kita perlu melihat hubungan dari setiap nilai covariance yang ada dengan mendapatkan eigenvector dan eigenvalue yang tetap memuaskan matriks covariance yang ada.<br>
Rumus eigenvector dan eigenvalue:
<img src="http://thumbnails115.imagebam.com/51545/a9db7f515444852.jpg" alt="Rumus eigen">
Dengan mendapatkan eigenvector, kita akan mendapatkan vektor-vektor yang bisa merepresentasikan matriks covariance. Sedangkan eigenvalue menunjukkan nilai atau besar dari eigenvector.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[82]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">eigenvalue</span><span class="p">,</span> <span class="n">eigenvector</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linalg</span><span class="o">.</span><span class="n">eig</span><span class="p">(</span><span class="n">covarianceMatrix</span><span class="p">)</span>
<span class="n">dfev</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">eigenvector</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Eigenvector </span><span class="se">\n</span><span class="si">%s</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">dfev</span>)
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Eigenvalue </span><span class="se">\n</span><span class="si">%s</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">eigenvalue</span>)
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>Eigenvector 
              0         1         2         3         4         5         6   \
0   4.250519e-02  0.999084  0.004866  0.001026 -0.000513 -0.000002  0.000213   
1   9.990941e-01 -0.042495 -0.002134 -0.000586 -0.000387 -0.000234  0.000131   
2   1.541582e-04 -0.000300  0.030933 -0.018685  0.187100  0.106555  0.508513   
3  -3.061344e-04 -0.000143  0.004331  0.008827 -0.118979 -0.905362  0.381429   
4  -7.123808e-05 -0.000136  0.012430  0.022363  0.036719  0.033276  0.296092   
5  -7.658603e-05  0.001229 -0.045645 -0.533964  0.817259 -0.086929  0.003324   
6   8.882439e-06  0.000036  0.000544  0.005855 -0.020917  0.024628  0.078401   
7  -1.020599e-04 -0.000082  0.025261 -0.073114 -0.022629 -0.046787 -0.166622   
8  -2.010861e-03  0.004920 -0.981019 -0.132846 -0.127350  0.009853  0.016226   
9  -1.987335e-04 -0.000222  0.161541 -0.722094 -0.399083 -0.153872 -0.331372   
10  6.751192e-07 -0.000009  0.001602 -0.002096  0.003000  0.007140  0.007330   
11 -2.180895e-04 -0.000223  0.087311 -0.411706 -0.324243  0.365626  0.603499   

          7         8         9         10        11  
0  -0.000177  0.000014  0.000033  0.000086 -0.000003  
1   0.000063 -0.000096  0.000129  0.000006  0.000005  
2  -0.768349  0.297129 -0.039163  0.115600 -0.014324  
3   0.122986  0.063345  0.034516  0.015826  0.000135  
4  -0.169271 -0.929718  0.074633 -0.098781  0.029372  
5   0.189672 -0.013719  0.007093 -0.033190 -0.001663  
6  -0.045722  0.144382  0.053030 -0.980234  0.078524  
7  -0.145065  0.041715  0.968596  0.050897  0.000344  
8  -0.056862 -0.005394  0.007286  0.005317  0.001753  
9  -0.344449 -0.089888 -0.178516 -0.032056  0.010636  
10  0.009800  0.023290 -0.002791  0.083311  0.996139  
11  0.429857  0.109088  0.136879  0.063877 -0.018830  

Eigenvalue 
[  6.79740128e-01   1.02647517e-01   7.07881762e-06   1.38104427e-06
   1.14397765e-06   1.24132313e-07   9.31436320e-08   4.02815625e-08
   9.37029900e-09   5.59159397e-09   8.43064176e-10   1.26830834e-11]

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kita sekarang mendapatkan 12 vektor dengan masing-masing nilai eigenvalue-nya. Terlihat bahwa eigenvalue pun ada 12. 
<a name="eigenvalue"></a></p>
<h2 id="Memilih-k-Eigenvector">Memilih <em>k</em> Eigenvector<a class="anchor-link" href="#Memilih-k-Eigenvector">&#182;</a></h2><p>Kita akan mengambil hanya <em>k</em> vektor sebagai <em>principal component</em> yang akan kita gunakan untuk analisis lebih lanjut. Untuk melakukan hal tersebut, kita akan melakukan plot terhadap eigenvalue. Kita memakai matplotlib untuk plot ini.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[84]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="n">plt</span><span class="o">.</span><span class="n">semilogy</span><span class="p">(</span> <span class="n">eigenvalue</span><span class="o">.</span><span class="n">real</span><span class="p">,</span> <span class="s1">&#39;-o&#39;</span> <span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s2">&quot;Log-plot of Eigenvalues&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span> <span class="s2">&quot;Eigenvalue Index&quot;</span> <span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span> <span class="s2">&quot;Eigenvalue Magnitude&quot;</span> <span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">grid</span><span class="p">()</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>


<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
Feecc84l2v8BsAmrwJSh82QAAAAASUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dengan memperhatikan hasil plot di atas, tampak ada 2 eigenvalue yang cukup besar dan signifikan. Sedangkan eigenvalue ketiga tampak berbeda cukup jauh dengan 2 eigenvalue teratas. Coba kita lihat eigenvalue dengan lebih dekat.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[85]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">dfeval</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">eigenvalue</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">dfeval</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>               0
0   6.797401e-01
1   1.026475e-01
2   7.078818e-06
3   1.381044e-06
4   1.143978e-06
5   1.241323e-07
6   9.314363e-08
7   4.028156e-08
8   9.370299e-09
9   5.591594e-09
10  8.430642e-10
11  1.268308e-11
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dua eigenvalue teratas bernilai 6.79 dan 1.03, sedangkan eigenvalue ketiga teratas adalah 1.02E-06 atau kira-kira 0.00000102. Perbedaan ini cukup besar. Secara matematis, tampak memilih nilai <em>k</em> = 2 adalah optimal, namun karena kita mereduksi dari 12 dimensi akan lebih baik untuk memilih nilai <em>k</em> = 3. Di sinilah, kita harus bisa mempertimbangkan tentang tujuan kita melakukan <em>dimensionality reduction</em>. Untuk pembelajaran, kita akan memilih <em>k</em> = 2 terlebih dahulu kemudian kita akan mendapatkan <em>feature vector</em>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[89]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Menentukan jumlah principal components</span>
<span class="n">nPrincipal</span> <span class="o">=</span> <span class="mi">2</span>

<span class="c1"># kita bangun vektor baru</span>
<span class="c1"># dari nPrincipal pertama eigenvector</span>
<span class="n">fv</span> <span class="o">=</span> <span class="n">eigenvector</span><span class="p">[:,:</span><span class="n">nPrincipal</span><span class="p">]</span>
<span class="n">dfNew</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">fv</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;New feature vector </span><span class="se">\n</span><span class="si">%s</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">dfNew</span>)
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>New feature vector 
               0         1
0   4.250519e-02  0.999084
1   9.990941e-01 -0.042495
2   1.541582e-04 -0.000300
3  -3.061344e-04 -0.000143
4  -7.123808e-05 -0.000136
5  -7.658603e-05  0.001229
6   8.882439e-06  0.000036
7  -1.020599e-04 -0.000082
8  -2.010861e-03  0.004920
9  -1.987335e-04 -0.000222
10  6.751192e-07 -0.000009
11 -2.180895e-04 -0.000223

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><a name="final"></a></p>
<h2 id="Mendapatkan-Matriks-Proyeksi">Mendapatkan Matriks Proyeksi<a class="anchor-link" href="#Mendapatkan-Matriks-Proyeksi">&#182;</a></h2><p>Kita telah memilih 2 eigenvector yang kini merepresentasikan 'permukaan' tempat proyeksi akan dilakukan. Tentunya eigenvector ini belum memiliki arti bagi kita, karena belum ditransformasikan kembali ke matriks nilai semula. Di sinilah proyeksi dilakukan. Kita akan transformasikan matriks hasil normalisasi dengan <em>feature vector</em> yang didapat.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[122]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Transformasikan data matrixNorm dengan Feature Vector</span>
<span class="c1"># transformedData = fv.T * matrixNorm.T</span>
<span class="n">transformedData</span> <span class="o">=</span> <span class="n">matrixNorm</span><span class="o">.</span><span class="n">dot</span><span class="p">(</span><span class="n">fv</span><span class="p">)</span>
<span class="n">dfTranformed</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">transformedData</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;Transformed data </span><span class="se">\n</span><span class="si">%s</span><span class="se">\n</span><span class="s1">&#39;</span> <span class="o">%</span><span class="k">dfTranformed</span>)
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>Transformed data 
           0         1
0   4.549690 -0.478930
1   2.957779 -0.361129
2   3.654173 -0.433452
3   2.970447 -0.380997
4   3.671871  0.772835
5   2.941583 -0.173099
6   2.186870 -0.391751
7   2.828338 -0.320701
8   5.217330 -0.502338
9   2.896971 -0.415051
10  3.004851 -0.422382
11  2.921954 -0.403250
12  2.666130 -0.422316
13  2.374419 -0.239589

</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kalau diperhatikan kini kita mendapatkan matris 14x2, artinya kita mendapatkan 14 negara dengan 2 fitur baru. Fitur baru ini yang disebut <em>principal components</em>. Sekarang kita akan melakukan plot terhadap data hasil transformasi ini.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[120]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">scatter</span><span class="p">(</span><span class="n">transformedData</span><span class="p">[:,</span><span class="mi">0</span><span class="p">],</span> <span class="n">transformedData</span><span class="p">[:,</span><span class="mi">1</span><span class="p">],</span> <span class="n">color</span><span class="o">=</span><span class="s1">&#39;b&#39;</span><span class="p">)</span>
<span class="k">for</span> <span class="n">country</span><span class="p">,</span> <span class="n">x</span><span class="p">,</span> <span class="n">y</span> <span class="ow">in</span> <span class="nb">zip</span><span class="p">((</span><span class="s1">&#39;Norway&#39;</span><span class="p">,</span><span class="s1">&#39;Australia&#39;</span><span class="p">,</span><span class="s1">&#39;Switzerland&#39;</span><span class="p">,</span><span class="s1">&#39;Netherlands&#39;</span><span class="p">,</span><span class="s1">&#39;USA&#39;</span><span class="p">,</span><span class="s1">&#39;Germany&#39;</span><span class="p">,</span><span class="s1">&#39;New Zealand&#39;</span><span class="p">,</span><span class="s1">&#39;Canada&#39;</span><span class="p">,</span><span class="s1">&#39;Singapore&#39;</span><span class="p">,</span>
                         <span class="s1">&#39;Denmark&#39;</span><span class="p">,</span> <span class="s1">&#39;Ireland&#39;</span><span class="p">,</span><span class="s1">&#39;Sweden&#39;</span><span class="p">,</span><span class="s1">&#39;Iceland&#39;</span><span class="p">,</span><span class="s1">&#39;United Kingdom&#39;</span><span class="p">),</span> <span class="n">transformedData</span><span class="p">[:,</span><span class="mi">0</span><span class="p">],</span> <span class="n">transformedData</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]):</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">annotate</span><span class="p">(</span><span class="n">country</span><span class="p">,</span> <span class="n">xy</span><span class="o">=</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="n">y</span><span class="p">),</span> <span class="n">xytext</span> <span class="o">=</span> <span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">10</span><span class="p">),</span> <span class="n">textcoords</span> <span class="o">=</span> <span class="s1">&#39;offset points&#39;</span><span class="p">,</span> <span class="n">ha</span> <span class="o">=</span> <span class="s1">&#39;right&#39;</span><span class="p">,</span> <span class="n">va</span> <span class="o">=</span> <span class="s1">&#39;bottom&#39;</span><span class="p">,</span>
                 <span class="n">bbox</span> <span class="o">=</span> <span class="nb">dict</span><span class="p">(</span><span class="n">boxstyle</span> <span class="o">=</span> <span class="s1">&#39;round,pad=0.5&#39;</span><span class="p">,</span> <span class="n">fc</span> <span class="o">=</span> <span class="s1">&#39;yellow&#39;</span><span class="p">,</span> <span class="n">alpha</span> <span class="o">=</span> <span class="mf">0.5</span><span class="p">),</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">8</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Principal Component 1&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Principal Component 2&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">grid</span><span class="p">()</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>


<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
U+3IkZ/avHm9bf/+CSWe4/PPr7CFC4eUaMvJecDmzett27ePLdH+1Vejbf78gSXazKbaL3/Zxc47
L6lE2+bNN9u8eb3L7Pu3v51jy5cnm9lU+/e/77SHHvpvW758uSUnJ9v+/ftLnPeDDz5ojz76aIm2
iRMnWnJysq1bt65E+zPPPGP33Xdfibb09HRLTk62Tz/9tET7vHnz7Pbbb7fSqvt+mJndfffd9tJL
L5Voq8l5bN++vVbn8eCDDzaI8zCr/fvx4IMPNojzMKvd+/Hggw82iPMw07+P4qpzHvPmzbPk5GS7
4IILrEOHDpacnGyXXHKJ4S1/MsgC6BNU9Kj2wnHOuZer2QEaW60nLPncbal6uf9vgFuAJ8zs5L7O
uWi8Kz/XmtlfK3mNFsBHwHEg2cxyKtl3ELB8+fLlDBo0qPon0gAdPHiQGTOmcPvtLenWLbHcfW67
bQFHjmTx2mtX06pVLPn5+bz66pecemoUrVplk58furs3f/bZIV5/fSfPPHNGjY5bv/4477wTw4UX
Vv/O1U2aNCUxsRN9+57BgAEDSEhIqGm5IiINXtgXjgukI1KD5z4IHKxqP+fcv4BE59zZZraisPlS
vFXPvqjkuJZ4V4IygZTKOitSM1u2HOIvf1nLf/4ziVatYsnNzWXVqjS6d99JdnY2kybtJiOjgOxs
Y8iQFjz00KkAvPXWIebPP0TbtjFs2JBJbGwUzz57Gl26xLJ/fy733rud9PT8Msfl5RlTp37L0qUn
SEyM5pxzmhMbm0+XLicqPa60w4cz6dgxh6FD91TrPM2MvLwC9u5dy8cf/x8ff3waN9xwNz169AhO
kCIiUqlAVroNGzNb75xbCPzBOfcTvK91ZgCpZrYHwDnXGW+NmFvMbFnhlZX/A+KAm/A6PEVPud9q
OMNJSkpL202vXm1p3boZZsaqVWlkZ29j8OBEYmPbcPHFHYmPj6agwPjhD9fw+efZXH99Em3bZrJm
TRarVg2ga9c47r//G+bOPcLzz/emY8cCFi1qXe5xzz67kz178tm06XzMYPjwr4iLa0LXrgl06FDx
caXt2xfFKac04aKLaj4FMTs7j7/8ZQOpqTMZO/Y+TqnsxlMiIhIU9XEKzI14C2gsAv4G/BP4cbHt
MUBvvPsdAQzGG5NyBrAZ2AXsLvxv+f/3u4HYuBE++MAbUBqI/Px8MjMzOXHiBLm5ueU+8vLyMTNy
c3M5cOAAR49+S58+LYmLa0JWVh733beFgQOXcdZZy1i+/ATLlx8nNzefvLwCLrigJZ06xZCbm8+5
57Zg8+ZMcnPzKz1u0aLD3HhjEgUFBZgVcOutSYWvn092dsXHlX7k5Xk1ZGbmVvtx8OBRMjNzadIk
iuuv70erVttYtuzfwX3T6oEDBw6Eu4SIoSw8ysGnLEKnXl1hATCzI8DNlWzfDkQX+31x8d8bg9rc
0O/w4cOsXLmStWvT2L//GzIy0vn44/c455zT2bmz7EyigoJsNmzYz4cfvkd+/gmysw+wenUznHO8
9tpxvvkmjyefTKRJE8dzzx3jm28Os3RpPps2ZZCensXSpVsA2LAhi4MHM1i6dAtz5x5ny5byjzt4
MJ1Nm/JYutRbIHnTpgyOHs2s8rjSNmzIYdmyKKZPL2dt/gps2rSJXr16AY6kpDbk5UFa2mJGjUom
OrrxfMTGjRunpccLKQuPcvApi9Cpdx0WqVpNbuhX3J49e5gzZyYFBevo0yeGoUMTyMyM5tix9vTq
5ejatewU7wED4khJac0LL2znwQdb0Lp1FK1bO/72t0z27s2jV68oBg507NuXz2efZTJqVDMGDIDV
q6FlSxgwwHueXbugeXPv96ZNrcLjRo1qygcfZHLvvc0oKIAHH8ys1nGl5eZCr16OMWOqP209Pf0U
4uMdWVkFbNv2LcuXZ7Ny5T6++eabwo5M4zBt2rRwlxAxlIVHOfiUReiEtMPinOsEfKdtW85u0YKk
qCjqxVKpp55K+4wMmD37Md59t8Z3D6gV5xyxsfGcemo/+vc/g/79+1e4Rkp5Nm6kRjf0K5KZmcmc
Oc+SkLCWW2/tR7Nm3vI6Bw9m0LFjIm3bxtK+fVy5rzlv3gB+85vt3HTTLpo2LcC5E1xySSzPP9+W
a6/dz7BhB+jcOZrLL29GfHwU7ds3pVWrHGJjvZ8BEhLyiIlxtG/flF/+MpHrriv/uJ/9LIbt2w/x
ve8doHXrKC6+OI7ly7OrPK601q2Ntm2j6NevebWzBX/fQYNaMnRoBg8/vJe5c1/ggQd+W6P3qT5r
7DPnilMWHuXgUxahE7IOi3Pu7N69+dF3vkOH888np3NnMmJiql7YLRIcPEjTlSshOTmHdu1Kr5UX
WmZGZuYxtmzZxDvvvM8XXwzl1lt/RHx8fNUHA1u2VL699A39iqxfv57MzI3cdVefk52V6oqOdkyb
1o0774wmLu44bdv6tX7xRacS++bnF/Dpp9u54ILm3Hab3xkcOTKekSO947p2bVLmuCJNmjiefbYt
R6dlNdIAACAASURBVI5kUVBgtGnT7OS2yo4rbdu2I+ze7XVkli3bRU5OPkOHdqneCReKj49m+PCW
LF26hY0bN3LGGTWbWi0iItUXkg6Lc65P//78+PbbaTFpEl9Xttx+JFq7Ftu3DwYObE+nTtX7Axhs
l1wCe/eeYM6cf/Daa47x4++p1k0Hq5plW/qGfkXWrl3Naafl06pVyasE3ms6qrteT5GcHGPjxlw2
bszjxIl88vO9448cyebYsWhyctLp3j2GqKjAVhI+cCCTggIjKan8NV7MoLK4li3LY/NmePnlXYUt
0WzYsOvk9qgoR/PmTejVqxl9+sQTF1f++PSWLZtw6qm5rF27Rh0WEZEQCsksodhYzhs2jPY//zmb
61tnJZJ06NCCa67pwu7daXz7bfVu19S7tzfAtvQY0Ohor72ioRaHDu2ic+dmZdpjY6PZv/8gmZnV
vzi2ZUsuTzxxhLfeOsr+/Sdo1iyLxMRsEhOzSUjIpE+faHr1iqJZswwSE7OJjU3HuaMn92nWLB0z
7/cWLTIxO0JBwRHy84/QpMlxWrTIJDExi9atsykoOEJMzHFatswkN/cwTZocp6DgCLGxJwqfp+jY
w8TGnjj5Gj17FnDBBXkkJh4hJ2cnmZn/ITHxCHFxBzh0aCt79mxh+fINvPjiOh5/fCtr1qSze/fu
cs+3U6dYDh3aVe62hmj27NnhLiFiKAuPcvApi9AJ+hUW51xcjx4MvuACDkXVx0nTEaZbt0RatPgP
a9eupUuX6n1lEcgN/XJzs4iJKfuGxcfHUFCQz5YtmfTv3xwzY/fuHHbuzCY720pcedm/P5PDh7P4
979P0LdvAaNGRZOQ4D9nXl4Bhw4ZSUlNyMpypKfn0LZtDJmZkJUFrVt7l0Sysx3p6dCmjePYsTyi
o5vw/9s77/Aoq+zxf86U9EpJCJAAoYTeuwiLgKJCbKsgqIBixcbuqlvVVb/uT107umth10rsgq5K
ExSRppQAQgAJEAgtkELqZMr9/fFOKqkwk0yS+3meeZL3fW8575k7854599xzg4ON6RulFCJCXp4V
l0uVeoScThcZGRAebiIw0L9cWQsguFyK06cLaNXKgtlswmSC+HgzAweaOH5ccDqFuDgzfn4WWrUK
wWIx4XIp1qw5yuHDeXz2WTrDhjmq9Lj5+ZkpLm7YqcPGZMuWLdxyyy2NLYZPoHVhoPVQhtaF9/DG
lFBkRAQRffrUnrlWUzsmk9Cxo4lTp07WuU5VG/p166YoLi6u1lNit9spLnZSWHj2FMunn2axe/dJ
goNNbN6cQ3Z2EYcOnSIuLrjUkAAoLCzgl19sxMUpevcWjhwp5vhxwWIxDJG8PCd2O+Tm2lAKCgsV
mZnG1I7DocjMLMIwcl04nYqCAhsOh4viYhcmkwOzWTCZBBHIynLi5wfZ2YbB5HJBYSEUFzsxtp4y
zhUXOymxqVwuyMuzoZRgs7kICnKQlnaG/PxilIJ16zJwOCAwULBYXLRta8JsdjJ2LDidxezfH47N
VqY/m82Qzel0QQtyJL7yyiuNLYLPoHVhoPVQhtaF9/CGweJnNmMOCcHhhbZbJH5+ZnJyCutdr3Nn
O7m5O9iwIZmkpGRcLhvVPViTk39m//5c1q9POetaWJidQ4ccPPTQL3TrZqFdOwthYQql7NjtZe0V
Fzuw2RR2O6xbBwUFCqsVrFbD21FUZBgNVqthUCgFZrMLEXGfN9oymSA6GuLiFOHh4HIZ1+12w1iw
WEyYzUaMSklsjOFNKTsGo7zJBGazyS2fYWDYbIKfn9Gf0+lAxNiny98fTCaFyyXk5pooLjYDipyc
AsDCsmUFHD6cT2BgSXtOMjIcFBfnk5d3kpiYbvTpY6zsqku8kUaj0WjqToPnYWnVivutVuzp6bxa
Et8SF8etDz/M8rlzOeTJvu65hyGffcbQ8s+O7GzCgoMpOHGCczaDx49/m/nzR5KYmOAJMQF44IHl
hIb68/DD4866di7PPrvdzqJF73Dw4Ao6d3Zw8cURhIT4Yapmnq5HD6FtW6FDh7M7KyyEqKhg/Pzy
6NFDsFqdFBYqgoOdmM2KggI7TqeLvDzo1AkGDQKz2TBcRBQiCrPZMFZKvB0lQbEmE1gsCqcTwEVx
MZw6Bdu3w5YtTnr2hMsuM8qKGG34+bmw2424HKOuwuEoadOF1Wp4ppxOcDjAZHLhchn/g+FBMZmM
9vLz7Tgcxv9Wq6AUhIQIhYXKPe0FZrOToUOF5GQYMcJJQkKJwQIZGUJRkSI9PZ/s7I/5+OOvGDTo
GhITr9BGi0aj0XiQxkgcpxwOzL/7HYNfeonN3uzo5ZfZ/PLLZX1s2kT4xInMfeQRvvZmv77A559/
Qnr6N8ye3ZFOnareZbk8OTnBxMTY6dz57LwkUVHQt6+FDh2CCAw0ExERwL59mURFBXDmjI2oqEDC
w/05diwfi8VGly5CaKiJnBwngYEm/PwEm82J02kYPxERZsxmyM934XAogoNN2O0uiooMb0xUFAwZ
Aunp8L//wbZtMHIkBAaCn58Ji0XIyXGWGiwmk2CxmCgqcuLvbyYnx0lkpBGDcuaMCxEICjIMmoIC
iIoy43Q6OXPGRWiomcBA3FNSLkJCTFgsLpSCuDhwOEy0a+dHYKCVyEgHsbEW+vQxpsFsNgfHjgk2
WwBRURGMHNmP7dtP8PnnHxASEsqECRPq/H6dOXOGXbt2sXv3dnJyTuBwFNOSppmqQsSEv38IsbEJ
9OnThy5durSojMIajaYijZLp9tZb+e7f/2bCY4+RHBFRceroxAn8pk3jkoMHibbbsSQkcOTrr/l6
3Toip0/n+pMnWQAQGsofLr6YzZ9+yuo336TTP//JuJQU3qmuz8xMLNdcw7Srr2b9XXdxAKCoCNO0
aYxPTqaLw4E5JobTn33Gl2BkYp0yZTFgbKT3+OPjmTKlx1ntJiXt4MUXN2K3u84qN3782wwdGsPG
jekcO5bHxIld+Ne/pgBw/Hges2cv5siRM7RvH0rr1kH06uWZxGP5+fmkpPzIpZdG1slYqY3iYjvh
4dCtWyRbthwjLi4cq9VEq1ZBHDuWj92uyM0tJifHgVKG1yQkxEJenouAABNBQWb3sZP9+x0sW+ZC
KUVxsWGEzJ1rJTPTDrjIzTW8HREREB4O2dnCli1w4YWKqKgy/eTluQgLMxMUZMZmc5Gd7cDhwL23
EYwf7+K55yz06KEIDTUTHGw86JzOYux2RUiIlVOnbLRpYy6NsSkqsmMyCWFh/jgcdrKzXdhsIGLG
ajVRXGyjttXd/ftHc/RoLlu3rmH8+PHVerTKk5qayqJFr6LUIbp2hX79ArFafffBvHLlSiZOnOj1
fpRS5Ofb+fXXDWzdGky3bhOYPv0GLBbfSdCdmJio07Cj9VAerQvv0Sif/NGjOfHDDxy4+25Gvvce
a8tfmz6di0eN4tB33xmGw7hxTL3zTkb897+sdziwbN5MWHo6gW3bkrl5M/HA6qVLiR82jNSa+pwy
hant2pH51lusKzk3dy6jg4MpPniQNwGuv56xN9/MhBdfZGu3brBgwZXExMRw6FA2I0cuJC3t/rMe
JJMnd+P66438G1WVS03N5vvvZ2OzOend+xU2bjzCiBEduffebxgxogNLl97A0aO5DBz4b3r1anP+
ygX27NmDUifp3buapCv1xGIx4e8PAQEWoqKCOXQop8L1vn3bEhho5cCBTPbvz6d166qHVX6+Ys0a
uPNOK2FhQkGBk9TUMns1JMQECEFBLsLCjAd9v36KtWtdHD0K7dtXLV9Ghp3ISEupUZKWZqtw/Vxm
Zlq1smI2OyksdJGSUkC7dn5YrRXvq8R4qTz107dvFBs2HCQtLY3OnTvX2E96ejqLFi2gS5fDXHNN
AgEBvvMwro4OHX5D166dGqw/pRS//prJRx99xccfW7j++mq3Emtw7r777sYWwSfQeihD68J7NNq3
47PPsnrSJG5NTa04LfTTT/Tcs4eO77zDKACHA4vFYmTI7duX1EWLiM/KIvDSS9m+ZAlD0tII2LyZ
+H/8g2+q6+u22xhx4ADtduwwDJMSfviBnkVF+HfoQG8ApxNzVBRZAFlZMHPmN2Rk2LBYTGRlFXLg
QDY9erSu0HZqahZ//etnHDlypspy06b1QUQICLAwcGA79u/PYsSIjnz77QGeffZiANq3D/VoPExm
ZiYREarCCp7zQcRU+lDu1CmcTZvSSxO+tWkTyIIFRwkMtOByuQgIcNG6dTHx8dbSmJMS8vMN4yGg
XIb/Nm2E/fud/PijYvx4RUGB8NZbissvd9G/v5CR4WLbNhg/Hk6cUNx7r4NDhxS5uYrERCf/+IcZ
lwt++kkxf77hPend25jiKeHECcUf/2jn0CHFmTOK4cMdvPWWmcBAoWvXYmbPNrN8uYujRxU33ig8
8YQRsGu1CsHBZsLDzeTkODCbK2YANlYHyVkGS/v2oUAamZmZtRosP//8M2FhB5g2rR8WS9PIA9C1
tuyEHkZE6N69NVOm2Pn88zVkZl5Gq1atGlSG6rj44osbWwSfQOuhDK0L79FoBsvIkeRceCE77r6b
sZV/AScl8dG4cWRWrnPhhRz49lu65+UR8MorLD1wgFYvvUTPjAxaXXcdVWbuWriQuEWLuPDrr1nY
pg2V1+zK3/7GN3ffXdE7s2sXMZ9+Cs8805Obbx4NQOvWT1NUdPbCp+nTP+Xppydy1VW9qixX/hez
2WzC4fD+7gR2u710xY0nKP/+WK1mOnYM48ABw8vSrVsrRAro1askky20bm1ixw47CQnGg/7MGQeR
kRbatoWYGHj++WI6dxaio4XYWEWnTiY++cRBaKiZlBQnUVGwZ4+iVy/FwYOGZ8Vuh1mz7PzlLxYu
vNBEerqNOXPg00+dXHSRmZkznbzwAlx0kYlly1zcUO5H+G23uXj4YQtjxgiHDxdz3XVGvSuvtKJU
MenpTj7/XMjJgeHDFfPmKcxmBwUFiowMI+g2ISGIkuXSJRQUOLBaQ3E6KxoaJpNgtUJxcXGNenU6
naSkbGTYsLAmY6w0Jr16teV//9vNrl27GDNmTGOLo9FoGphG/ZZ86SXWrFlD/+xsQkvODRtGysMP
c0FxMQKQlkbAmjVEAtxwA6m//EL8qVNEjBtH5oQJHPjPfxjXvTtpVYUKbN1K6Pz5XPvooywZO9bw
nJRnzBhS/v1vRmZmGoZbZiaWpUtpC0Yis44dDbHee287WVlVLyvOzi6ic+eIWstVZtKkeBYu3ArA
sWO5fPnl3jrVqys1rVDp0uVFtm8/Uee2xo/vXGp4jR9/nORkP37zm05ERARgNpuwWEz07RtFnz5t
CQ01ExVlon17EydPumjf3o+iIhO7dzvYs8fJkCHC7NlWunUz8+uvLj78EG66qZjvvzdWBWVmwujR
wokTkJtr5JHx94djx2DlSsUtt9hJSLAxcSIcPGgYNsnJhlHVuTPs3+9i/HgLXboYUzY//6xYvVpx
6612evUqJjFRSE836pV4gCZPFqKjrSQk+NO1q3DggCIqyo+oKCtt21rp3z+kdLoJjGBhk+kQBQWK
oKCQanRdu8GYm5tLYeFJ4uLC6/xetGT8/My0bw8nTtR97Go0muZDgxss5b/bu3WjcOpUNubmElJy
7sMPWebnh6NTJ+5o3547LriAm375hQiAXr3IDwsjLyGBwwA33sjB3FxCR42qOn7l979nbFER/i+8
wEUdOnB7x47cXvIX4L//ZW3v3hzt25db27fnjn79mLt2LdFgpLG/9dYVDBnyOsnJxysEr5a/hxde
uIRrrvmo1nJn15vMhg1H6Nv3VWbPXsKECV3qq0qPImKsqqmKvLy8OrVhMpkwmcw4HBAUJOTnK9LS
nJjNwuDB/gwd6k9wsIkzZ5wMGWJmzBgTEREAQkyMcOwYHD8OsbHQpg3s2gUhIRATYyqdWlqxwkJK
ih/vvgvr15v54x/NBAUZeVX69fMnIcGvNC6mZKkzwPbtVlJS/NmwwUpSEjz4oJnt2+2IQI8ellKj
w2wuW/5cGYfDictlBBiLgMUSTlhYGC6XqlNwbWVsNhtgrGxqSqSknJ2rp6Hw91duvfkGixcvbmwR
fAKthzK0LrxHg08JnT7Ni+WPk5JYk5TEmpLjqCjsK1ZUH4+Sns6/y5e123miurKrVvEV8FV11/38
UB99xHfAd+XP79pFTP/+8Mor15emYn/mmbJ5yVWrZpX+P3Nmf2bO7F96XF05gI8+urb0/3btQli6
tHGDB48ezeW++5ayZ88pbLZCJkzw59VXI8nLc/K73+1n+/Y8iopcxMTYeOaZs1cbJSXl8+KLZ0hP
d7JwYQYPPRRKhw5mzGYLV19dSHw87NrlJCMDhg93cv/9xrJiiwXmzSsmNdXIz9K1qyI62jBYAgMN
o6FjR9iyBXr1gowMRViYsbHjiy866dfPgZ8frFjhICAArr3WRH4+PPCAjfh42LMHDhww4lD8/Y39
kx5/3Mlf/uLigw+cHDwIy5cX06OH0VdxsYt9+5ysWOEiOxsWL7azYwdMmmQEAeflFbNzp5MVK+y8
+24GV15p7Crdrl0MZrOZoiInVuvZ+zDVlZq8YZ99tpsnn/wBl0tRVOSgQ4cwVqy4sU7t3nrrF9xw
Q3/GjevMkiUpxMSEMnx4h3OWs4QdO3bQs2dPwPDWLVkynf79o8+73RKuvfZjpk7twU03DTjrmgj1
3ojTmyQlJXHllVc2thiNjtZDGVoX3sMbBotLKZTTic6a5SGcToXJ5Llf4SXPxxtu+IzJk7vx8cfX
cuDAAXbtWo/Lpfj97/czdmw4r79uLM++6qqtvPtuIU89VTFHy+TJAVx/fTAvvHCEMWMiufzy07z/
vh9WqxWXC06cgNdeg3bt/Bg3zk5BgZUTJxw8/7yL9u0V8+YZ+wU98IBi2DAzdruDuDgAE3FxLr7/
XhEfb+bnn42l0jNmONm+XfjoI+OBFR0Nr70WwJ49Rdx0EyxdKqxeDbGxipgYsNvN+Pu7mDVLsWOH
MHSoC6UEEcWTT5rIzjYS1YlYEVGcPm0jOFiYMsWP4GAX69Y5GTPGSlZWAOvX5zBmTCiTJ8ewfHkB
kIfZbMbpdJGZ6aJTJ8+s8CrP8eN53H77/9i69XY6dgwDYNu243Wu/8YbiaX/L168h4EDoz1isFx7
7bU+ZTQ0Jh9++GFjiwAYRpzNZsNur3r3cm/z5ptvkpubW+fyxkKEAJ9aou4pfGVMNEe8MVoKi4oo
PnEC/4QECrzQfovjzBkHoaFhHm0zN9fG2rVppb/Wo6KiOHQojIMHs1m8+BQbNpzh2WeNHaKzs20E
BJxtMKWmOvjrX0+RnOxk4cIscnJcHDumOHXKTnGxYuZMf6KiICvLwYABZk6fNjNzZgDz55/hiy9C
yc8vIiTETGKiE7PZxLXXmigsdGAymWjVCu65R9GqlQWTyYmIMT306qtBfPNNITEx0Lu3hfbt/fn4
4yLatIE77xQcDiO/y4QJ0K+fH7/+6iA0FN5/PwSlFCtWFLFjRzHp6ZCXB48/DoMG+ZGW5qRVKzvb
thlxSydOONmwIR+LxcyxY9CjRxA2mz/BwcHMm9eKp58+glKKgwezcblCiIqK8uj7Y8iQh8ViIiKi
bFnVwIHtWL58P889t56lS28gN9dG69ZP869/Xc4ttwzmnXeS+eGHQ7zxRmJpRmar1cQXX+xh5cpU
3n47mbvvHk56+hk++ywFEWNTyp07T3Lo0P3Exobz7LPr+PjjXTgcLqKignnttSnExobz979/x44d
J8nLK+bIkTMsX17R0/P88+v54INfsNudWK1mXnxxMiNHdgQMT8xNN/VnxYpUTpzI5+abB/KXv4wF
YM+eU9x88xecOWOjW7dWFBQ0zkO3KbJ//362b08mJWUjNlsO4P2gfs8ggIX27XvRp88gBg0aRFBQ
UGMLpfFxvGGwnD5+nAObNtG7qkBXTf3Izy/m8GELU6bEe7xtESmN8QgODiY+vj+pqVtwOl0sXNiV
wYMjMJmELVvSCQrKOav+9OmnePrpSNLS7JjN8NBDsG+fjf79zYSEmGjVykxcnIVDh+DMGRt79zrZ
urX25Gt1wepeYWw2Q2SklZwcOwMHQmiolexsO126BBMaaubXX8vq7NhhJy3NwdChMG5cKBs32vjl
Fxvbt+cTFuZP+R97xtRD2bFSCperZP8i46Gwa1cGGRn+dOs2gMDAc58Sqo7+/aO54IJYOnV6gXHj
OjF6dCwzZvRj7NhOXH/9p9jtTlavPsjw4R1YsSKVW24ZzMqVqVx+efcK7Vx6aXcSExMYNKgd9947
ovT83/5mbANx++1fMnJkR2Jjw0lK2sGePadZv/4WRIT33tvOnXd+xf/+NwOADRuOsG3bHbRpc/bD
5aabBjB//igANm48wuzZS9i9e17p9ZwcG+vW3cLp0wV07foSN988iJiYUG688XPuumsYs2cPZOfO
kwwd+jozZ/bzuD6bG+vXr2fZsv/Qtu1pRo0Ko23bIKxWa+0VfYCypIBrWL36e5KTRzNr1m0EB5+d
aVujKcHjBotSSonIz2vWMGjqVIK0l+XcUUrx/feHEIkpjRnwTLsQGurP2LGdePbZdTz0kLFENCio
Dd27D2PMmAweffQI8+cXY7UK+/fnEBhYQGCgoqjIxcmTRRw6pMjMdOLnZ+fKKyP5/PMiCgvzaNvW
QnS0BaWKyctzkJOjiIgwERpqol07M926WfjNb4p55ZVC/vhHK8ePK774ws7cuRZatbKSkeGkuNhF
YKAAQlGRcRwebkXEQW6uHYdDERFhITTURHZ2MQkJZpKT7QQHW4mIMBERYebUKTsBAU7atbOyd28x
2dnFZGU58PeHAQMCOXnSxubNNsLChM6d/ThyxInTqcjONpYi5+a63AG2DgICLOzaVcDhw8LOndms
WnUGgLy8DiQkxJfGOXkaEeGTT65j797TfP/9Qb7++leefPIHfvrpVgYObMfatWmsXJnKn/40hvnz
l6GUYtWqA/zzn3XPA/HEE2s4fPhMqUGyePEefv75KIMHvw6Ay6UqBItfdln3Ko0VgM2bj/Hkkz9w
+nQhFouJvXtPY7M58Pc3vmZmzDCMkNatg4iPj+TAgWxCQvzYtu04s2YZ8Sp9+0YxZkxcvXXV0ti9
ezfLli1kzJhiJkzo12T3rRo8OIZTpwp46601LFrkx9y5dzXZe9F4H2+tElr7/ff88Ne/0vXDD2l/
8iRNw+z3EZRSpKXl8PnnKWzaFMjkyTM9+suj5Pvg3Xev4qefjtK376sMHvwar7yyiQ4dOvDeezfR
oUMcd999kjvuOMGjj2aRnR1KZGQsVqs/ISFtiYyM5amn4pg3r4ArrsgnNTWI2Fg//PxCKCwMwmy2
4O8fRGBgOIGB4VgsflitxvHzz7diyxYTF1xg5557XIwfH4DFEkBAQBgWix9msx8Wi3/py2y24u8f
jMlk7C1jNpvx8ytrOyYmgiuuiGTdOheLF9v57LNiUlKEoKBw/P2DEDETGBjOoEGROJ0W3n23mC+/
dNKpUyAmk5XAwLJyVms4IuFYLCGle9l07tyJ2Nh2rFpVwDPPZNOhQzwgDB8+2mvGSnl69GjNrbcO
4fPPpzFiREe+/HIvEyd2YeXKVH74IY3x47vQr1807723ndatg4iKqttYeffdZJYs2cOnn15XmghQ
KcWf/jSGrVtvZ+vW20lOvoNt2+4orRMS4lflKgi73ck113zEc89dwo4dd7JmzWwAbLay3DXV5SRq
yg+oOXPmNEq/W7f+TGxsFhMmdPEJ/Z3Pypg2bYJITOxIevoWMjIyPChV49BYY6Il4JWIJ6VUvoi8
+b//kbVtG8M6dKBrZCRmf/9zS5Pe0BQVEXHyJCi1n8jIs/LXeRWXS1FYqLDbQwkN7c3UqVMYMmSI
R/tITb2v9P9PPrnurOshIf689toVpcdfffUlnTsXEhYWxpo1ZbLMnRvG3LmdS49fegm2bz/O6dOn
WLWqXelD0OinbBVJp06wfPnZv9KdThdms9m9qWFZzIzZ7MLPz4/7748FYM6ckLPqJiT4k5BwdpxP
9+7+dO9unPf3h9mzq566iY/35+qrwyj7vvTn6qv9cDohNDQMl6uYmTOjeOyxqwD4f//vsirb8SRH
j+Zy8GA2o0cb921kUc6ia9dIoqNDmD79Ezp1iiAoyMqECV14+OHvuOqqqj1xYWF+5OQUlR5/+20q
jz++hh9+mENgYNnviSuv7Mlzz63nmmt6ERkZWBrfMnBgu9IyVWW6LSpyYLc7iY01dP3SSxvrdI+h
of4MGtSOt99OZvbsgfzyy0l+/PFwlSuEfJHGyGpqs9nYv/9nJk2K9AljBc4/+3HXrpEEBBxl165d
XokHAyNR44EDBzhy5AhFRUW1VzhHoqOjWbp0qdfarytms5mQkBC6d+9OmzaeXxTQGHgtRFsplQ+8
IyKf/PorPYAwb/bnYboDE2+88bf06HH2hofeRETw9/enY8eOxMbGntMXkslkwumsvVxd6d49gczM
rSilapWnU6cIkpPz2bGjgO7dAwgKqvvqpqraVkrhdBqrhLzJqVPGTtLlKShwcuyYPz//nMmhQ6HM
nDm8Tm2VyHy+Ows7HC4ee+x7Dh7MJijIisPhYs6cgUydmoDLpcjJsTFxopG/Z9KkeO655xsmTiyL
dSqvzhtvHMDs2YtZvHgP8+YN4733tlNY6ODSS99HKaPs11/PZMaMfmRmFjJ+/NulMtxyy6AKBku/
fv3O6iM01J8nnriIYcPeoG3bYKZP71PhXmrKSfT221cyZ84SnntuPd27t2bcuIbbp+h8uf766xu8
zzNnzuB05tK+ve8kHCw/Js4Fs9lEVJSQleWdsMeNGzfy3XdLKCw8THBwAYGBUuEHlSeJi4PU1P1e
abs+OByK3FxYtiyC6Oi+XHPNDK8Zgw2F6OWJZyMig4HNmzdvZvDgwY0tTr1Zu3YtP/zwAg8+GN2q
ggAAIABJREFU2Buz+fyf9FlZWSQnf8egQYGEhwfUoXwhO3cew+ksIjjY5f5yqFtfGRl5BAcrgoKM
Cnl5itdec9GvXxCxsd6xdx0OyMysfE5x9KiNvXtb0bNnB2bOHETv3m3r1F5uro1nnz3Atdf+jT59
+lRb7sSJE/zrX39k7tzI0mXLmppJStqBUlczY8bMxhal0Th69Civv/5nbr+9NTExobVXaCK8995O
rNZrmTZtmkfbXbduHcuXv8mQIYUMG9aB6Ohgn/FMeRuHw8Wvv2ayevVR8vL6MmvW3Q1itGzZsqVk
ZmCIUmqLp9ptKh4PTT3o1q0bK1eGc+BANt26nf8mcREREQQFRbNrVxoDB7auMIVQFZGRgYwe3ZnM
zEJOny6kuNhRYTPCmsjLs5CdnUunTv4A7NnjoKDARHBwG/LyvONmycuDI0fKjpVS5OXlc+ZMJFFR
o5gxI47evev+Udm9+xQmU1vi42te2WVkx5VqMwxrzsblkvP2XDUPqvd2du78AkFBVnbuvKvUizBs
2Bs8++zFjB3ry94rz38O8vPzWbEiidGj7Uya1KPFGColWCwmevZsQ1xcOAsXbmflyuXMmOE7u53X
F22wNEOio6Np3bon3323ntjYsNJVGufK4cOHGTBgCNu2KTZtSicyEiIj/bFaa39wlM8hUhesVjNp
aTYiIkz4+Zk5etTJmDERTJ3qPfd3URHs3Akul4vi4mKyspxkZsZSWDgMaM2mTRAfDxkZacTF1byC
JTfXxvr1GcTHX1XrUueAgADASl5ezZsk+hppabXrwVvk5SnatfP8EvJzZe3atT63EaOIYLM5efPN
Ldx227nFvxnxZHX/gdCYY6Imdu/ejcgJxozp3mDGii/qIijIyrBhbVix4ieKin7r/u5pejQ5g0VE
IoEFwBSMLEmfAve5Y2bqUv8b4BLgSqXUF14TtBb27oX9+6FbNyN1vCcREa6+egbvvpvJW2/tZMSI
dvTo0ZrAQMs5fWh//PFHrr/+egYPHs7Jkyc5efI4Bw6cwuWqZtOd88DlCuTkyXC2bTtNerqLwsIQ
rrginJQU737ZpKdDTo6V4uLWOBwxQDRgrLY5fBg+/RTM5h+r/SLKyysmJeUU69Zl4HQO4bLLptba
Z0hICG3adGPv3s11nm7yBX78sXo9eJMzZ2wcO2Zh5MjODd53dTz99NM+Z7AAPProOP7851XcdNOA
CquzMjLyueOOr9i37zQAd989vNSo6dLlRaZP78OqVQfp0aM1TqeLK65IYNq0vrzyyiZ+//vlZGU9
RGCglYsuepvHHx/PyJEdufzyRezbd4SgoHAGDIjmjTemEhhoZcqURdx4Y3+mTesLwPLl+3n44dVs
2DC3wfSQmppKbKyToKCGW6jaWJ+P2khIaM3SpUc4fPgw3T390GkgmpzBAizCeJpMAPyAt4DXgFr9
XCIyH3DiDd9jHcnMhBkzYNmysnOXXAJJSRAZ6bl+OnTowI033s3y5V+xZMk2lPoVs9mB2Vz/B7/D
0Ysnn9xZ7ow/0AGllEeSwFXsS+F0diU9vYiCAhexsYFs3uzAz8+EN9+24mLYsEE4dUqAAuDAWWUm
TuzFwYM7zzrvdCocDgsmU1u6dEnk8suvoFWr2qfiRITevYewceNGxowpqDa/ia/x29/+tsH7VEqx
dm0aZnN7EhISGrz/6vjggw8aW4QqGTCgHRdd1IXnn1/Pn/50Yen5e+75hp49W/Ppp9eRkZHPkCGv
M3Bgu9ItG06fLmTjRsOg+M9/trJiRSrTpvXl228PMHRoe77//hC/+U1nduw4yciRHTGbTSQlXUNI
iAWr1cpdd33Fyy9v4sEHL+D++0fyyCPflRosr776U4XEhQ1BYWEuoaENO4XYGJ+PuhAa6g8UU1DQ
dFOjNSmDRUR6YnhHhiiltrrP3QN8JSJ/UEpVu9GKiAwA7geGAXXfkMXDzJgBK1dWPLdyJVx/PXh6
JVyHDh2YM+c2cnNzOXjwIIWFhbhcvp2622w2ExwcTJcuXfDz8+PQoUNkZmZSXOydaZO0NMO70q0b
hIXBH/5QfdkZM2DUqOpljo+Pr3d68REjRpCSksxbb61h8uQYevRojZ+fb8doNGQ2VaUUGRkFbNx4
hM2bg5g8eZpPubN9OZ38Y4/9hhEj3uT224cChi5Xrkzl6advB6Bt22CuvroXK1emlhoss2cPLK0/
aVI8jz32PS6XYteuDJ58cgIrVuzHZBKGD++A2WxCKcWzz67n66/34XC4OHPGVroMf+LEeObPX0Zy
8nEiIwP56aejfPzxtTQkSrlqXA1U1eaiy5ffwJQpSbzwwiV079663n36arZhQw+qSe8D1qQMFmAU
kFVirLhZifHTewSwpKpKIhKI4ZmZp5Q62ViBV3v3VvSslOB0Guf37fP89BBAaGjoeS87bCzi4+Nr
DV49F6rydNXm2U9M9Pz7ExwczKxZt/HRR8F88slmLJYUIiIUVmvTTqjmCVwuRUEBnDkTQEBAZy67
7CqGD6/b0nKNkWJgxox+PPHEmtJl5CJSYy6skBC/0v9jY8Px97fw/vvbGTq0PRMmdOGJJ9ZgNptK
l9MvWrSD7747yA8/zCE42I+XX97I6tUHS9u4997hvPTSRqKjQ7j55oF1intrKKrbXFRE+OqrGY0s
Xe3UN86oOdDUDJZ2wMnyJ5RSThHJdF+rjueBtUqp/3lTuNrYX8vS/F9/9Y7Bojmbqjxd69dD69aQ
nU2FPDZmM0yc6L33Jjg4mDlzbiM7O5uUlBSys7NxODwfH9TUKMlJFBcXR3x8fLPc2dfb/OUvF9Kr
1yv4+ZkRESZOjOe11zbzxBMXkZGRz+efp/DJJ9V7PUoSEj766DjCwwOwWs188skuFi+eDkBWVhFt
2gQRHOxHbq6Nt95KplOnsgD5G27oz9//bnhpfvrpVq/fb32obnNRMOJ5liyZTv/+0Ywf/zZDh8aw
cWM6x47lMXFiF/71rymAYfTMmrWY9PQzdOwYRmRkIL16teHhh8exatUB/vrXVdhsToqLncyfP5Kb
bx4EwJw5SzCZICXlNKdPFzBqVCz//vfl+Ptb6hVn9O67V/Hee9tZsGATDoeLkBA/XnrpUvr3j6Y5
4hPfACLyD+ChGooooFdNTVBNgIOIJAIXAQOrut6Q1JYMslu3hpGjvjzwwAM888wzjS2GR9i7F77/
vnpP1+nThqdl7dqy8xMnGjFG3tZDREQEI0eO9Fr7nqI5jYfzxRd1Ud6D0rp1EPfeO4JHHvkOgJde
mswdd3xF//7/AuBvfxvLsGEdzqpXwqRJhoEzYYLh5Zw4sQsLF24tfSDedNMAlizZQ1zc03Tu3Jax
Y+M4dKhso9TAQCtXX92LY8fy6NDBt3INVbe5aPv2Z+e2SU3N5vvvZ2OzOend+xU2bjzCiBEduffe
bxg9uiOPPPIbTpzIY+DA17Bas4FxDBkSw48/3oyIkJVVyKBBrzF5crfS9jdtOsrGjXMJDLRw5ZUf
8vzzG/jjH8fUK85o3brDJCXt5Icf5mC1mlm7No0ZMz5l5867GkyPDYmv+JP+CfSs4dULSMWIPamQ
9UZEzEAkcKKatscD8UCOiNhFpGTv+s9EZFVNQl122WUkJiZWeI0aNeqsfTOWL19OYmLiWfXnzZvH
woULS4979IBRo7YAicCp0vNmM3Tt+gifffZUhfppaWkkJiaSkpJS4fzLL7/MAw88UOFcQUEBiYmJ
rC3/pAWSkpKq3Nti2rRpdb6PDRs2VLgPMBIDJSYmcurUqQrnH3nkEZ56qvb72LsX7rzzZebObZj7
yMyEuLh5JCQs5LbbKtwJld+PP/8Z5s17hDlznmLvXiO2KDISbLYQRo5MZOnSxn0/Ko8rOP/3oz73
ERcX1yzuA87//YiLi2vw+5g9ezYnTlRwNLNjx45SeVNT7ys1KD7++GN++9sonM6HGTu2E23bBvP0
00P4058i2L79TubOLUuM+fLL3XA40iu0O3JkBO+9151WrYzftv/3fxM4fvwPrF69mrVr1xIW5s+K
FTfy8cfj+PLLqxk+PIvXX59QWt/pdLFs2W5Gj65oDdntdpKSkkhLS6tw/scff/TKuDp27BhJSUkV
Ak5FhHnz2vLyywO59NJu/PjjYfr2fZVt2w6Rn59XIevutGl92LRpE2vWrGLgwHbs329c+/bbA7Ru
nUZaWhrR0SFMmdKdgIAAduzYwaJFS/jtbz+mX79/cdFF75CZWcirr35S+j5fd11vgoKspKam0q1b
LitXpgKwcmUqt98+lK+++orDh/eUxhkZ+nTSoUNG6X0sWZLC9u0n6N37BXr0eJZ77vmG7OwibDYH
OTk5JCUlnTUGk5KSPPr5SEpKKn02tmvXjsTERObPn39WHU/QpDLduoNufwGGlgu6vRj4GuhYVdCt
iEQBlTdS2AncA/xPKXWoijpey3SblWUE2Hp7lZCv0lCrpCozebIxBVSXLQv27q04/dNYMms0VdFU
MiR/+eUe7rnnG6ZM6cGCBbXvvfX22zsJDp7u0VU2b731BmFhK7n66poc9GVceun7XHxxPC+/vInF
i8umhObPH0liorE67dprP2bq1B7cdNMAWrd+muTkO0rfh1tv/YLY2HAefngckya9y+WXd+f++w2v
6ZAhr/PII+NITExgzpwlxMdH8Le/jQMMw2PBgp9YseJG2rR5mq1bbyc21phau//+pURFBfPnP19Y
YaoK4MEHV+DnZ+aJJy6q9d5cLsVjj/3ClVf+lYEDvTvh4K1Mt77iYakTSqkUYBnwhogME5ELgJeB
pBJjRUTai8huERnqrnNSKbWr/Mvd3OGqjBVvExlp/GLfuxe+/poKv+BbAjWtkvIWJcHOtRkrZrNh
iFSOVWkMmVsSe/fCN98YQeea2jF2bvcnO9t7G/h5gqlTEzh48P46GStKKbKzlUd3pa+No0dzWbfu
cOlxVlYhBw8a2cHr+jt+woQu/Oc/xhqQkyfz+eqrskGcnV1UGs+zZs0hkpMr/p7+5JPdFBTYcTpd
/Pe/25g0yZh2mzSpK6+/vhmgNM6o5Fplrrgigfff38Hhw8Y0nFKKzZuP1k34JohPxLDUkxkYieNW
YiSO+wS4r9x1K9ADqGm9YaO7lbp3b3kBto21Sqq2YOcSSmJVytNYMrcEtOfq3AgJCSEmpje7d/9I
375NezO7Ek6cyCcrK6hBE5pVtbno7NkDmDo1gfvuK8sxUdPGnS+8MJnZsxfTt++rtG8fysiRHUuD
eP/xjwncdddXPP74GgYObMfIkR0rtDNsWHsuvvhdTp0qYPToWO67z8hR8+KLk7nzzrrFGV1wQRxP
PTWRq676EKdTUVzs5PLLuzNkSHtPqMjnaHIGi1IqmxqSxLm9JjWunVNK+c7auiZASkoKPXv2PO92
GmuVVG3Bzm+8AePGVd13RZlTMEKqymiJK7s8NR4aMieRt/CULupLnz6DWb36R1JTs4iPb3zr7tSp
U7RpU3nmvW44HC5WrDhIYGAvunTp4mHJqicuLpylS6t+lKSmlv0GXrVqVoVrH31UtqqqVatAvvlm
JmaziczMQkaOfJM77zQS5U2cGM/evfdU23///tG8+ebZMThRUcF8+ul1tcpVwnXX9eG666rfZLU5
0aSmhDSNw4MPPuiRdhprlVSPHsYv98p75pVMAc2dW73RUVHms/Xgqyu7vIknxkN103TlPVdNAU99
NurLyJEj6dLlUpKSjrJyZSrHjuXicDReUsgVK1bUq7xSivz8YpKTj/PWWztIS+vEtdfO8crGlt6M
09y37zRDh77BwIH/5sIL/8vddw/n1KnttdZrjBRLTSletTqanIdF0/AsWLDAI+2UGA6Vg1+9necE
jGmGysHOVU0BVaaizGV6aAiZfRVPjIfmkpPIU5+N+mKxWJg+/QaWL49iy5Z1rF2bBqQh4mqUhIMF
BfHs23f2thXVoRQoZQEiiYubzMyZl9C5c2ePy+XnF4TNVodI+3OkX79otm69vcK5nJzaPW7/+c8V
3hKpWgw9WPDz86u1rK+iDRZNrXhyI69zNRzOl5Jg5337jIdhfTadLJO5TA8NIbOv4onx0FRzElWm
MTe5s1gsXHbZZVxyySUcPnyYnJwc7HZ77RV9ABEhICCA2NhYwsK8t9IpKiqaLVsULpeqMUW/JwkP
997O8udDWloOEEpUVNONe9IGi6ZBOR/DwROcS7BzY8vcHGlMb1tzw2w2e8U70Rzo3bs3a9dG8Ouv
mfToUf99gZoLSim2bz9BVNToc4418gV0DIumUejeHS69tGk9mJqizL5MUpJhnJSnJXuuNJ4nJiaG
uLgRfPZZeunS35aGy6VYvfogu3aFMnLkuMYW57zQHhZNrTz11FM89FBNOye0DLQeDDylh+bgudJj
wsBX9SAizJw5m3ffdbFw4Q+0a3eIrl2DCQqyei3WJzk5mQEDBnil7frgcLjIzi4iJaWYgoI2TJp0
k8cToTY02mDR1Er5dNYtGa0HA0/roSnnJNJjwqA6PezdawRYN6Yx6u/vz6xZc9m3bxy7du3kl1/2
YLMVoJR3VlWtXetPTk7jT7uYzVaCgyMZPHgAffr0ISYmprFFOm+aVGr+hsKbqfk1Go2muaOTArZs
dGp+jUaj0TQJ9HYWGm+gDRaNRqPReIzmkhRQ43tog0VTK5W3J2+paD0YaD2UoXVhUF4PdUkK2JzR
Y8J7aINFUys333xzY4vgE2g9GGg9lKF1YVBeD80lKeC50tBjoiXtdq4NFk2tPProo40tgk+g9WCg
9VCG1oVBeT3UtndXU10RVlcaakxkZsLkyZCQAJddZuh98mTIymqQ7hsFvUqoCvQqIY1Gozl3srLO
3oJDrxLyLJMnV58purF3O/fWKiGdh0Wj0Wg0HqU5JAX0ZUoCmytTPrC5OepbGywajUaj8QpNOSmg
L9NcdjuvLzqGRVMrCxcubGwRfAKtBwOthzK0Lgy0HspoCF201MBmbbBoamXLFo9NQTZptB4MtB7K
0Low0HoooyF00VIDm3XQbRXooFuNRqPR+DK+HNisg241Go1Go9EALTOwWRssGo1Go9E0UVpSYLOO
YdFoNBqNRuPzaINFUyuJiYmNLYJPoPVgoPVQhtaFgdZDGVoX3kMbLJpaufvuuxtbBJ9A68FA66EM
rQsDrYcytC68h14lVAV6lZBGo9FoNOeGt1YJaQ+LRqPRaDQan0cbLBqNRqPRaHwebbBoamXx4sWN
LYJPoPVgoPVQhtaFgdZDGVoX3qNJGSwiEiki74tIjohkicibIhJch3qjRORbEclz1/1ORPwbQubm
wFNPPdXYIvgEWg8GWg9laF0YaD2UoXXhPZqUwQIsAnoBE4DLgbHAazVVEJFRwDfAUmCo+7UAcHlV
0mZE27ZtG1sEn0DrwUDroQytCwOthzK0LrxHk8l0KyI9gUswoo63us/dA3wlIn9QSh2vpupzwAtK
qWfKndvnXWk1Go1Go9F4kqbkYRkFZJUYK25WAgoYUVUFEWnrvnZKRH4UkePu6aALvC+uRqPRaDQa
T9GUDJZ2wMnyJ5RSTiDTfa0q4t1/H8GYOroE2AJ8KyJdvSSnRqPRaDQaD9PoU0Ii8g/goRqKKIy4
lWqbcJepihKD7N9KqXfc//9ORCYANwN/qaZeAMDu3btr6LblsGnTJrZs8VjunyaL1oOB1kMZWhcG
Wg9laF1UeHYGeLLdRs90KyKtgda1FEsFbgT+qZQqLSsiZqAI+K1SakkVbXd2171BKbWo3PkPALtS
6sZqZJoBvF+/O9FoNBqNRlOOmeWfvedLo3tYlFKngdO1lROR9UCEiAwqF8cyAcPDsrGatg+KyFEg
odKlHsDXNXS3DJgJHMQwiDQajUaj0dSNAKAzxrPUYzS6h6U+iMjXQBRwJ+AH/AfYVOIpEZH2wLfA
jUqpn93n7gMeBeYC24DZwO+AvkqpAw18CxqNRqPRaM6BRvew1JMZGDlUVmLkUfkEuK/cdSuG9ySo
5IRS6kV3krjngFZAMjBRGysajUaj0TQdmpSHRaPRaDQaTcukKS1r1mg0Go1G00LRBotGo9FoNBqf
p8UZLCLyJxHZJCJnROSEiHwuIj3qUO9aEdktIoUikiwilzaEvN7kXHQhIrNExCUiTvdfl4gUNJTM
3kBE7nC/pznu1zoRmVxLnWY3HqD+umiO46Eq3J8Vl4g8V0u5ZjkuSqiLHprrmBCRR8rdT8lrVy11
mt14qK8ePDkeWpzBAlwIvIyRsn8iRqDuchEJrK6CewPFRcAbwEBgMbBYRHp7X1yvUm9duMnByC5c
8urkTSEbgMMYyQuHuF+rgCUiUmXCwmY8HqCeunDT3MZDBURkGHArRsB+TeWa87iosx7cNNcxsROI
puy+xlRXsJmPhzrrwY1nxoNSqkW/gDYYK47G1FDmA+CLSufWA682tvyNoItZQGZjy9oAujgNzGnJ
46GOumjW4wEIAfYAFwGrgedqKNtsx0U99dAsxwTGFi9b6lG+WY6Hc9CDx8ZDS/SwVCYCI7V/Zg1l
RmEspS7PMvf55kRddAEQIiIHRSRNRJrLLwYARMQkItMxlsavr6ZYixgPddQFNOPxALwCfKmUWlWH
ss15XNRHD9B8x0R3EUkXkf0i8p6IxNZQtjmPh/roATw0Hlq0wSIiArwArFVK1TQX2Q44UencCarf
dLHJUQ9d7MHYhykRIxuwCVgnIh28L6X3EJG+IpIL2IBXgauUUinVFG/W46GeumiW4wHAbawNAv5U
xyrNclycgx6a65jYgJF49BLgDqALsEZEgqsp3yzHA/XXg8fGQ1NLHOdpXgV6AxecQ92aNl1sitRJ
F0qpDRgDFijdMmE3cBuGq7CpkgIMwPAyXQO8IyJja3hQV6Y5jYc666K5jgcR6YhhwE9SStnPpyma
8Lg4Fz001zGhlCqfZn6niGwCDgHXAf+tYzNNejxA/fXgyfHQYg0WEVkAXAZcqJQ6Vkvx4xgBRuWJ
4mzruUlST11UQCnlEJGtQDevCNdAKKUcGBtlAmwRkeEYWZTvrKJ4sx4P9dTFWXWbw3jACDhuC2x2
ex8BzMBYEbkb8FfuCfpyNMdxcS56qEAzGhMVUErliMheqr+v5jgezqIOeqhc/pzHQ4ucEnI/oK8A
xiul0upQZT3GRovlmUTN8/pNgnPQReX6JqAvUC9DpwlgAvyrudZsx0M11KSLCjSj8bAS6IexumOA
+/Uz8B4woJqHdHMcF+eihwo0ozFRAREJAbpS/X01x/FwFnXQQ+Xy5z4eGjviuBEinF8FsjCW9EaX
ewWUK/M28GS541FAMcamiQkYmykWAb0b+34aQRd/w/jQdcGY104C8oGejX0/56GH/8NYltfJ/UH6
B+AALnJff6cljIdz1EWzGw816KbC6piW8j1xDnpolmMCeAYY6/5sjAZWYHhLWruvt4jviXPQg8fG
Q0ucEroDYw7xu0rn52AoGiAWcJZcUEqtF5HrMb7M/w/YB1yhag5ObQrUWxdAJPA6RuBYFrAZGKXq
Huvhi0Rj3G8MRr6A7cDFqmxFREeMhzbQrMcD1FMXNM/xUB2VvQkt5XuiMjXqgeY7Jjpi5FVpDWQA
a4GRSqnT5a63hO+JeukBD44HvfmhRqPRaDQan6dFxrBoNBqNRqNpWmiDRaPRaDQajc+jDRaNRqPR
aDQ+jzZYNBqNRqPR+DzaYNFoNBqNRuPzaINFo9FoNBqNz6MNFo1Go9FoND6PNlg0Go1Go9H4PNpg
0Wg0Go1G4/Nog0WjaaKIyH9F5DMPtjdLRDI91V65dl0ikujpdjUaTctCGywaTSPjNjxcIuIUEZuI
7BORv7p3Na2Je4HZHhTlA6CHB9urMyISLSIvi8h+ESkSkUMi8oWIXNQY8vgqdTVSReRCt/7StcGo
aS60xM0PNRpf5BsM4yMAuBRjJ2078FTlgm5DRimlcj0pgFLKBtg82WZdEJFOwDogE/gDsAOwApOB
BUDvhpapGRAMbAP+A3zayLJoNB5Be1g0Gt/AppTKUEodVkq9DnwLJAKIyGwRyRKRqSLyC8YW9bGV
f22LyGoReVFEnhKR0yJyTEQeKd+JiISLyGsiclxECkVku4hcVr6fcmUfEZGtInKbiKSJSL6IfCgi
oeXKDBWR5SKSISLZIvKdiAyq573/C2O332FKqc+VUr8qpXYrpZ4HRpbrK1ZElohIrojkuGWJqkLe
OW4PTa6ILBARk4g86NbHCRH5cyWduETkDhH5WkQK3F6eayqV6Ssi37qvn3LrMLjc9f+KyOci8nsR
Oeous0BEzOXK+InIP0XkiIjkich6ERlX7vos9/t8sYjscsv/jYhEl9wfMAu4opxHbmxVClVKLVVK
PayUWgxIPd8PjcYn0QaLRuObFAJ+7v8VEAQ8CNwC9MHY1r0qbgLygOHu8g+LyAQAERFgKTAKmAH0
Av6IYSyU9FN5+/ZuwLXA5cAlwCAM708JocBbwAXACGAv8HX5h3lNiEiku90FSqmiyteVUmfKHS4B
IoALgYlAV4xprPJ0xfDMXAJMB+YCXwHtgbHAQ8ATIjKsUr3HgI+B/sD7wAcikuCWMRBDb6eBIcBv
3f2/XKmN8UA88BuM92E2FafsXsHQ0XVAP3d/34hI13JlgoDfAzPd9xkH/NN97Z/AR25ZooEYDM+U
RtMyUErpl37pVyO+gP8Cn5U7nohhsPw/9/EsDKOiby31VgPfVyqzEXjS/f/FGNNMXauRYxaQWe74
EaAYiCl37hJ3G1HVtGECcoDLyp1zAYnVlB/mvn5FLTqa5Jalfblzvdx1h5STNxcIKlfmG2B/pbZ2
Aw9Wkm9BpTLrS84BtwKngIBy1y8FHEDbcu9FKiDlynwILHL/H+fWW7tK/awAnqj0Pncud/1O4Gh1
73kdx1e1+tcv/WpKLx3DotH4BlNFJBcjdkOARcDfy10vVkrtrEM72ysdHwNKpk0GAEfNAhoCAAAD
XUlEQVSUUvvrIVeaUupYueP1gBlIAE66p2T+Dxjn7scMBGI8oOtCyXRFZc9OZXoCh5VSR0tOKKV2
i0g2huGy2X36oFKqoFy9ExiGBZXORVU6t6HS8XoMfZX0nawqeoB+xDDOEijzdv2ilCp/H8eAvu7/
+2LoZq/b01WCH4YxVEKBUupgpTYqy6rRtEi0waLR+AargDswfoUfVUq5Kl0vrGM79krHirKp37q2
UROq0t93gEjgHiANI2h3A2XTWbWxz91WL+CLGsoJVRs1lc9Xdf816aQmStqtrm+ove+SfkIwDKfB
GB6P8uTV0oaOQdFo0DEsGo2vkK+UOqCUOlKFseIptgMdRaRbPerEiUi7csejMaYt9pQ7fkkptUwp
tRvjgdumro0rpbKAZcA8d6xIBUQk3P3vLrcsHcpd6w2Eu6+dLyOrOE4p1/fASvKNwdDD3jq2vxXD
wxKtlEqt9DpZDzmL3e1oNC0ObbBoNC0EpdQa4AfgUxGZKCKdRWSyiFxcQzUb8LaI9BeRC4EXgQ+V
UiXTIPuAG0Wkp4iMAN4DCqppqzruwngIbxKRq0Wkm7u9e3EHlSqlVmIsd35fRAaJyHDgbWC1Umpr
Pfurimvdq4u6i8jfMWJrFrivvY+xMuttEekjIuOBl4B3yumhRpRS+zCm+d4Rkavcuh8uIn8UkUvr
IedBoL+I9BCR1iJSpZdcRIJFZICIDHSfincfx9ajL43Gp9AGi0bTfKgtDgTgauAnjIfnLxh5Xmr6
xb4P+Az4GmN1yjZgXrnrN2NMCW3BMCBeBCp7DGqUyx2zMRgjaPifGIbJcoxVN3eUK3oFkAV8777+
K8ZKoPpSlTyPuNtKBm4ApiulUtzyFWIEG7cCNmGs1FmBMQ1WH2ZjTKH9E8N78zkwFGMqra68geHd
+hlDz6OrKTcUw6uzGeN+n8V4j/5eTXmNxueRijFiGo1GY+DO+3GFUmpwY8viTUTEBVyplKophkaj
0TQy2sOi0Wg0Go3G59EGi0ajaeloN7NG0wTQU0IajUaj0Wh8Hu1h0Wg0Go1G4/Nog0Wj0Wg0Go3P
ow0WjUaj0Wg0Po82WDQajUaj0fg82mDRaDQajUbj82iDRaPRaDQajc+jDRaNRqPRaDQ+jzZYNBqN
RqPR+Dz/H/D6oyLpEibjAAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Makna-Principal-Component-Analysis-(PCA)">Makna Principal Component Analysis (PCA)<a class="anchor-link" href="#Makna-Principal-Component-Analysis-(PCA)">&#182;</a></h1><p>PCA menggunakan aljabar linier untuk melakukan proyeksi keseluruhan data dengan tujuan mempertahakan informasi relevan yang ada di dalamnya. Hal ini dibuktikan secara matematis maupun penjelasan intuitif (yang sebenarnya pakai matematika juga). Sumber yang sangat jelas menjelaskan <em>behind the scenes</em> dari PCA bisa dicek di:</p>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Principal_component_analysis">Artikel PCA di Wikipedia</a></li>
<li><a href="http://stats.stackexchange.com/questions/2691/making-sense-of-principal-component-analysis-eigenvectors-eigenvalues">Q &amp; A di Stat.StackExchange</a></li>
</ul>
<p>Keduanya komprehensif. Di wikipedia berfokus kepada aljabar liniernya, sedangkan di stackexchange ada penulis yang menjelaskan secara intuisi dan logika. Pemahaman matematik yang baik diperlukan di sini. Misalnya, eigenvektor yang didapat itu menunjukkan vektor arah yang baru dan eigenvalue yang didapat menunjukkan nilai besar vektor tersebut. Dengan memilih <em>k</em> eigenvektor, berarti kita akan mendapatkan <em>k</em> fitur baru yang biasa disebut <em>principal components</em>.</p>
<h2 id="Kelemahan-PCA">Kelemahan PCA<a class="anchor-link" href="#Kelemahan-PCA">&#182;</a></h2><p>Harus diakui bahwa fitur baru yang didapat cukup susah untuk diinterpretasikan dan dimengerti. Kita bisa melihat dari plot terakhir yang digambar bahwa muncul hubungan yang lebih mudah dilihat, namun maksud dari fitur di sumbu x maupun sumbu y susah dipahami. Walau demikian, PCA sering sekali dipakai di berbagai kompetisi data science, seperti di <a href="https://www.kaggle.com/">kaggle</a>, karena kecepatannya dalam mereduksi fitur.</p>
<h2 id="Seleksi-Fitur">Seleksi Fitur<a class="anchor-link" href="#Seleksi-Fitur">&#182;</a></h2><p>Hal menarik adalah pasti kita pernah berpikir seandainya kita tidak menyerahkan 'semua' proses dalam <em>dimensionality reduction</em> ini kepada mesin. Sebenarnya ketika memilih <em>k</em> fitur, kita sudah menggunakan intuisi kita walau banyak dipengaruhi oleh nilai matematis yang dihasilkan. Sebagian pakar lain mengganggap kemudahan dan kecepatan PCA bisa mengurangi pemahaman akan model yang dibangun. Semisalnya, hasil keluaran PCA akan digunakan untuk analisis biaya premi asuransi, maka kita akan kesusahan untuk menjelaskan fitur apa saja yang digunakan, karena kita hanya punya <em>principal components</em>.
Sebagia analis dan data scientist tidak menggunakan PCA, melainkan seleksi fitur atau <em>feature selection</em>. Seleksi fitur menggunakan pemahaman domain kepakaran untuk memahami masing-masing fitur yang ada sebelum melakukan reduksi. Di contoh kita tentang human development berdasarkan GDP, berarti kita harus memiliki pemahaman yang baik tentang dunia ekonomi dan pembangunan, sebelum melakukan seleksi fitur. Bernard Flury di bukunya <a href="https://www.amazon.com/First-Course-Multivariate-Statistics-Springer/dp/038798206X/ref=sr_1_1?s=books&amp;ie=UTF8&amp;qid=1479448846&amp;sr=1-1&amp;keywords=bernard+flury">A First Course in Multivariate Analysis</a> berpendapat bahwa memang metode terbaik untuk melakukan reduksi fitur membutuhkan <strong><em>subjective choice, careful thought, and some experience</em></strong>.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>
</html>
