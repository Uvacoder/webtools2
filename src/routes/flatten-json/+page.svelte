<script lang="ts">
  import flat from 'flat'
  import Heading from "../../components/Heading.svelte";
  
  let input = "";
  let output = "";

  let keepTopLevelArray = true;

  const flatten = () => {
    if(!input) return;

    try {
      const parsed = JSON.parse(input);

      if (keepTopLevelArray && Array.isArray(parsed)) {
        let newArray: any[] = []

        for (const item of parsed) {
          newArray.push(flat(item))
        }

        output = JSON.stringify(newArray, null, 2);
        return
      }

      output = JSON.stringify(flat(parsed), null, 2);
    } catch (e) {
      output = "Invalid JSON";
    }
  }
</script>

<Heading>
  Flatten JSON
</Heading>

<div class="grid grid-cols-2 gap-4 mt-6">
  <div>
    <h2 class="text-xl font-bold">Input</h2>
    <textarea
      class="textarea textarea-bordered w-full mt-2"
      placeholder="Paste JSON here"
      rows="10"
      bind:value={input}
    />
  </div>

  <div>
    <h2 class="text-xl font-bold">Output</h2>
    <textarea
      class="textarea textarea-bordered w-full mt-2"
      placeholder="Flattened JSON will appear here"
      rows="10"
      bind:value={output}
    />
  </div>

  <div>
    <h2 class="text-xl font-bold">Config</h2>
    <div class="flex items-center gap-2">
      <label for="keep-arrays">Keep top level array</label>
      <input id="keep-arrays" type="checkbox" bind:checked={keepTopLevelArray} class="checkbox" />
    </div>
  </div>
</div>

<button class="btn btn-primary mt-4 w-full" on:click={() => flatten()}>
  Flatten 🚀
</button>
