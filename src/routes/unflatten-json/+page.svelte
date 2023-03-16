<script lang="ts">
  import flat from 'flat'
  import Heading from "../../components/Heading.svelte";
  
  let input = "";
  let output = "";

  const unflatten = () => {
    if(!input) return;

    try {
      const parsed = JSON.parse(input);

      if(Array.isArray(parsed)){
        let newArray: any[] = []

        for (const item of parsed) {
          newArray.push(flat.unflatten(item))
        }

        output = JSON.stringify(newArray, null, 2);

        return
      }

      output = JSON.stringify(flat.unflatten(parsed), null, 2);
    } catch (e) {
      output = "Invalid JSON";
    }
  }
</script>

<Heading>
  Unflatten JSON
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
      placeholder="Unflattened JSON will appear here"
      rows="10"
      bind:value={output}
    />
  </div>
</div>

<button class="btn btn-primary mt-4 w-full" on:click={() => unflatten()}>
  Unflatten 🚀
</button>
