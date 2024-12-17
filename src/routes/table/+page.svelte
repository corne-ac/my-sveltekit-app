<script>
    let { data } = $props();
  </script>

<div class="flex justify-center items-center flex-col">
    <div class="overflow-x-auto">
        <table class="table table-lg">
          <!-- head -->
          <thead>
            <tr class="text-lg text-neutral-200">
              <th></th>
              <th>Title</th>
              <th>Description</th>
              <th>Number</th>
              <th>Date</th>
              <th>Time</th>
            </tr>
          </thead>
          <tbody>
            {#each data.items as item}
            <tr>
              <th>{item.id}</th>
              <td>{item.title}</td>
              <td>{item.description}</td>
              <td>{item.number}</td>
              <td>{item.date}</td>
              <td>{item.time}</td>
            </tr>
            {/each}
          </tbody>
        </table>
        
        <div class="flex justify-end items-end pt-10">
          <a href="/table/add" class="btn btn-neutral hover:btn-primary">
            Add Row
          </a>
        </div>
      </div>

      
</div>