<script>
  import { LayerCake, Svg } from "layercake";
  import { description } from "./data/data";

  console.log(description);
</script>

<main>
  <div class="key-container">
    {#each description as d}
      <div class="key" key={d} data-tooltip={d.description}>
        <div class="pill" style={`background-color: ${d.color};`} />
        <div class="label">{d.name}</div>
      </div>
    {/each}
  </div>
</main>

<style>
  main {
    width: 100%;
    height: 100%;
  }

  .key {
    align-items: center;
    display: inline-flex;
    margin-right: 8px;
  }

  .pill {
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    vertical-align: middle;
  }

  .label {
    font-size: 13px;
  }

  [data-tooltip] {
    position: relative;
  }

  [data-tooltip]:before,
  [data-tooltip]:after {
    visibility: hidden;
    opacity: 0;
    pointer-events: none;
    transition: 0.2s ease-out;
    transform: translate(-50%, 5px);
  }

  [data-tooltip]:before {
    position: absolute;
    top: 100%;
    left: 50%;
    margin-top: 5px;
    padding: 7px;
    width: 100%;
    min-width: 70px;
    max-width: 250px;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
    background-color: #000;
    background-color: hsla(0, 0%, 20%, 0.9);
    color: #fff;
    content: attr(data-tooltip);
    font-size: 14px;
    line-height: 1.2;
    transition: 0.2s ease-out;
  }

  [data-tooltip]:after {
    position: absolute;
    top: 100%;
    left: 50%;
    width: 0;
    border-bottom: 5px solid #000;
    border-bottom: 5px solid hsla(0, 0%, 20%, 0.9);
    border-right: 5px solid transparent;
    border-left: 5px solid transparent;
    content: " ";
    font-size: 0;
    line-height: 0;
  }

  [data-tooltip]:hover {
    cursor: pointer;
  }
  [data-tooltip]:hover:before,
  [data-tooltip]:hover:after {
    visibility: visible;
    opacity: 1;
    transform: translate(-50%, 0);
  }
  [data-tooltip="false"]:hover:before,
  [data-tooltip="false"]:hover:after {
    visibility: hidden;
    opacity: 0;
  }
</style>
