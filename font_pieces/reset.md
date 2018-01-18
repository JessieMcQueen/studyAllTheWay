##reset清除默认

```
/* reset */
article,
aside,
audio,
blockquote,
body,
button,
dd,
div,
dl,
dt,
fieldset,
figcaption,
figure,
footer,
form,
h1,
h2,
h3,
h4,
h5,
h6,
header,
hgroup,
input,
legend,
li,
menu,
nav,
ol,
p,
pre,
section,
td,
textarea,
th,
ul,
video {
    margin: 0;
    padding: 0;
}

table {
    border-collapse: collapse;
    border-spacing: 0;
}

em {
    font-style: normal;
}

fieldset,
img {
    border: 0;
}

address,
caption,
cite,
code,
dfn,
em,
optgroup,
th,
var {
    font-style: inherit;
    font-weight: inherit;
}

del,
ins {
    text-decoration: none;
}

li {
    list-style: none;
}

caption,
th {
    text-align: left;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-size: 100%;
}

q:after,
q:before {
    content: '';
}

abbr,
acronym {
    border: 0;
    font-variant: normal;
}

sup {
    vertical-align: baseline;
}

sub {
    vertical-align: baseline;
}

body,
button,
input,
select,
textarea {
    font-size: 100%;
    outline: none;
}
// 为解决IE11中，input默认的叉和密码默认的小眼睛
input::-ms-clear, 
input::-ms-reveal {
    display: none;
}

textarea {
    resize: none;
    outline: none;
}

cite,
i {
    font-style: normal;
}

.clearfix {
    zoom: 1;
}

.clearfix:after {
    content: "";
    display: block;
    clear: both;
    height: 0;
    visibility: hidden;
}

a {
    text-decoration: none;
}

a:focus {
    outline: none;
}

.hide {
    display: none !important;
}

.fr {
    float: right;
}

.fl {
    float: left;
}

.block {
    display: block;
}

.bold {
    font-weight: bold;
}

.center {
    text-align: center;
}

.auto {
    margin-left: auto;
    margin-right: auto;
}

```

对于IE中，textarea默认有一个不知名的框，直接将textarea的overflow:auto, 这个不知名的框就没了。。应该是scroll的时候自带的框。
