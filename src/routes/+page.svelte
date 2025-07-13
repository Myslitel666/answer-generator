<script>
  import { TextArea, TextField, IconHover } from "svelte-elegant";
  import { themeStore } from "svelte-elegant/stores";
  import Plus from "../components/Plus.svelte";
  import Delete from "../components/Delete.svelte";

  let theme;

  // Подписываемся на изменения темы
  themeStore.subscribe((value) => {
    theme = value;
  });

  let inputs = [
    { id: 1, value: "" },
    { id: 2, value: "" },
  ];

  function addNewOption() {
    // Находим максимальный существующий ID
    const maxId = Math.max(...inputs.map((input) => input.id));
    // Добавляем новый элемент с ID на 1 больше максимального
    inputs = [...inputs, { id: maxId + 1, value: "" }];
  }

  // Функция для отладки - можно удалить в production
  function logInputs() {
    console.log("Current inputs:", inputs);
  }

  function removeOption(id) {
    inputs = inputs.filter((input) => input.id !== id);
  }
</script>

<div style:height="37rem" style:display="flex" style:padding="4.35rem 0 0 1rem">
  <div
    style:display="flex"
    style:flex-direction="column"
    style:height="100%"
    style:width="67.5%"
    style:align-items="center"
    style:padding="1rem"
    style:gap="0.5rem"
  >
    <p style:font-size="1.28rem">Ask your question:</p>
    <TextArea width="100%" variant="Filled" height="6rem" label="Question" />
    <p style:font-size="1.28rem">Give me response options:</p>
    {#each inputs as input, index (input.id)}
      <div style:display="flex" style:width="100%">
        <TextField
          width="100%"
          label="Answer {index + 1}"
          bind:value={input.value}
          oninput={logInputs}
        />
        <button
          onclick={() => removeOption(input.id)}
          style:margin-left="0.33rem"
          style:margin-right="0.33rem"
        >
          <Delete />
        </button>
      </div>
    {/each}
    <button
      onclick={addNewOption}
      style:align-self="flex-start"
      style:display="flex"
      style:align-items="center"
      style:cursor="pointer"
    >
      <Plus />
      <span
        style:margin-left="0.5rem"
        style:color={theme.palette.primary}
        style:justify-content="center"
        style:font-size="0.94rem"
      >
        Add a new response option
      </span>
    </button>
  </div>
  <div
    style:width="32.5%"
    style:height="37rem"
    style:background-color="#e7e7e7"
  ></div>
</div>
