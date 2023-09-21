<script>
  let note = "A";
  let steps = 0;
  let transposedNote = "";
  let transposedNotes = "";

  const notes = [
    "C",
    "C#",
    "D",
    "D#",
    "E",
    "F",
    "F#",
    "G",
    "G#",
    "A",
    "A#",
    "B",
  ];

  function transpose(note, steps) {
    const index = (notes.indexOf(note.toUpperCase()) + steps) % notes.length;
    let result = notes[index < 0 ? index + notes.length : index];
    transposedNotes += " " + result;
    return result;
  }

  function crop(){
    transposedNotes = transposedNotes.slice(0, -1);
  }
</script>

<select bind:value={note}>
  {#each notes as noteOption}
    <option>{noteOption}</option>
  {/each}
</select>

<input type="number" bind:value={steps} placeholder="Enter number of steps" />

<button on:click={() => (transposedNote = transpose(note, steps))}>Transpose</button>

<div on:click={crop} on:keydown={crop}>{transposedNotes}</div>
