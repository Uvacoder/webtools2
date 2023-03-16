<script>
  import Heading from "../components/Heading.svelte";
</script>

<Heading>
  Web Tools 🔧
  <span slot="description">A collection of useful web tools</span>
</Heading>

<div class="flex justify-center gap-4 mt-4">
  <div class="card w-96 bg-base-100 shadow-xl">
    <div class="card-body">
      <h2 class="card-title">Flatten JSON</h2>
      <p>
        Tool to flatten a JSON object
      </p>
      <div class="card-actions justify-center w-full">
        <a href="/flatten-json" class="btn btn-primary w-full">
          Launch
        </a>
      </div>
    </div>
  </div>
  <div class="card w-96 bg-base-100 shadow-xl">
    <div class="card-body">
      <h2 class="card-title">Expand/Unflatten JSON</h2>
      <p>
        Tool to expand/unflatten a JSON object
      </p>
      <div class="card-actions justify-center w-full">
        <a href="/unflatten-json" class="btn btn-primary w-full">
          Launch
        </a>
      </div>
    </div>
  </div>
</div>
