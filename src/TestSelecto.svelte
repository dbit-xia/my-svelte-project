<script>
    import Selecto from "selecto";
    const selecto = new Selecto({
        // The container to add a selection element
        container: document.body,
        // The area to drag selection element (default: container)
        // dragContainer: window,
        // Targets to select. You can register a queryselector or an Element.
        selectableTargets: [".target", document.querySelector(".target2")],
        // Whether to select by click (default: true)
        selectByClick: true,
        // Whether to select from the target inside (default: true)
        selectFromInside: true,
        // After the select, whether to select the next target with the selected target (deselected if the target is selected again).
        continueSelect: false,
        // Determines which key to continue selecting the next target via keydown and keyup.
        toggleContinueSelect: "shift",
        // The container for keydown and keyup events
        keyContainer: window,
        // The rate at which the target overlaps the drag area to be selected. (default: 100)
        hitRate: 100,
    });

    selecto.on("select", e => {
        e.added.forEach(el => {
            console.log('added');
            el.classList.add("selected");
        });
        e.removed.forEach(el => {
            console.log('removed');
            el.classList.remove("selected");
        });
    });

</script>

<style>

    .target {
        position: absolute;
        width: 200px;
        height: 150px;
        line-height: 150px;
        border: 1px solid #333;
        font-size: 30px;
        text-align: center;
        box-sizing: border-box;
        z-index: 20;
    }
    .target.selected {
        border: 4px solid #f55;
    }
</style>
<div>
    <div class="target selected">selected</div>
    <br/>
    <div class="target" style="left: 100px">target</div>
    <div class="target" style="left: 300px">target</div>
    <div class="target" style="left: 500px">target</div>
    <div class="target2">target2</div>
    <div class="target2">target2</div>
    <br/>
    <br/>
    <br/>
    <br/>
    <a>end</a>
</div>

