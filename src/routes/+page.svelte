<script>
  import { TextArea } from "svelte-elegant";
</script>

<div style:height="37rem" style:display="flex" style:padding="4.35rem 0 0 1rem">
  <div
    style:background-color="#f7f7f7"
    style:display="flex"
    style:flex-direction="column"
    style:height="100%"
    style:width="67.5%"
    style:align-items="center"
    style:padding="1rem"
    style:gap="0.5rem"
  >
    <p style:font-size="1.36rem">Ask your question:</p>
    <TextArea width="100%" variant="Filled" height="6rem" label="Question"
    ></TextArea>
  </div>
  <div
    style:width="32.5%"
    style:height="100%"
    style:background-color="#e7e7e7"
  ></div>
</div>
