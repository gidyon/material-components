<template>
    <div>
        <div>
            <h2>Bottom</h2>
            <p class="tooltip--bottom" data-tooltip="Hello World!">Short</p>
        </div>

        <div>
            <h2>Left</h2>
            <p class="tooltip--left" data-tooltip="Hey">Short</p>
        </div>

        <div>
            <h2>Right</h2>
            <p class="tooltip--right" data-tooltip="Hello World!">Short</p>
            <p class="tooltip--right" data-tooltip="Hello World!">Loooooooooooooooooong link</p>
        </div>

        <div>
            <h2>Triangle</h2>
            <p class="tooltip--triangle" data-tooltip="Hello World 1!">Short</p>
            <p class="tooltip--triangle" data-tooltip="Hello World 2!">Loooooooooooooooooong link</p>
        </div>

        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css">

        <link href='https://fonts.googleapis.com/css?family=Roboto:400,500,600,700' rel='stylesheet' type='text/css'>
    </div>
</template>

<style lang="scss" scoped>
$pink: #e91e63;
$paper: #efefef;
$clouds: #ecf0f1;
$teal: #009688;
$yellow: #ffeb3b;
$cubic: cubic-bezier(.64,.09,.08,1);
h1 {
  font-size: 26px;
  background: $pink;
  color: $paper;
  padding: 40px 0 40px 20%;
  margin-bottom: 50px;
}
p {
  display: inline;
  margin-right: 50px;
}

[class^="tooltip"] {
  position: relative;
  &:after {
    opacity: 0;
    visibility: hidden;
    position: absolute;
    content: attr(data-tooltip);
    padding: 6px 10px;
    top: 1.4em;
    left: 50%;
    transform: translateX(-50%) translateY(-2px);
    background: grey;
    color: white;
    white-space: nowrap;
    z-index: 2;
    border-radius: 2px;
    transition: opacity 0.2s $cubic, transform 0.2s $cubic;
  }
  &:hover {
    &:after {
      display: block;
      opacity: 1;
      visibility: visible;
      transform: translateX(-50%) translateY(0);
    }
  }
}

.tooltip--left {
  &:after {
    top: -4px;
    left: 0;
    transform: translateX(-112%) translateY(0);
  }
  &:hover {
    &:after {
      transform: translateX(-110%) translateY(0);
    }
  }
}

.tooltip--right {
  &:after {
    top: -4px;
    left: 100%;
    transform: translateX(12%) translateY(0);
  }
  &:hover {
    &:after {
      transform: translateX(10%) translateY(0);
    }
  }
}

.tooltip--triangle {
  &:before {
    content: '';
    width: 0;
    height: 0;
    border-left: solid 5px transparent;
    border-right: solid 5px transparent;
    border-bottom: solid 5px grey;
    opacity: 0;
    visibility: hidden;
    position: absolute;
    transform: translateX(-50%) translateY(-2px);
    top: 1.1em;
    left: 50%;
    transition: opacity 0.2s $cubic, transform 0.2s $cubic;
    z-index: 3;
  }
  &:hover {
    &:before {
      display: block;
      opacity: 1;
      visibility: visible;
      transform: translateX(-50%) translateY(0);
    }
  }
}

</style>

