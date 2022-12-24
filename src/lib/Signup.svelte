<script>
  import { createForm } from "svelte-forms-lib";
  // @ts-ignore
  import * as yup from "yup";

  const { form, errors, state, handleChange, handleSubmit } = createForm({
    initialValues: {
      username: "",
      password: "",
      email: "",
    },
    validationSchema: yup.object().shape({
      username: yup.string().required(),
      password: yup.string().required(),
      email: yup.string().required(),
    }),
    onSubmit: (values) => {
      alert(JSON.stringify(values));
    },
  });
</script>

<main>
  <h2>SignUp</h2>
  <form class="form-container" on:submit={handleSubmit}>
    <input
      class="text"
      name="username"
      type="text"
      placeholder="username"
      on:change={handleChange}
      on:blur={handleChange}
      bind:value={$form.username}
    />

    {#if $errors.username}
      <small>{$errors.username}</small>
    {/if}

    <input
      class="text"
      name="email"
      type="email"
      placeholder="email"
      on:change={handleChange}
      on:blur={handleChange}
      bind:value={$form.email}
    />

    {#if $errors.email}
      <small>{$errors.email}</small>
    {/if}

    <input
      class="text"
      name="password"
      type="password"
      placeholder="password"
      on:change={handleChange}
      on:blur={handleChange}
      bind:value={$form.password}
    />

    {#if $errors.username}
      <small>{$errors.password}</small>
    {/if}

    <button class="primary">Signup</button><br/>
    <a href="/login">Already have an account ?</a>
  </form>
</main>

<style>
  .form-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .primary {
    background-color: black;
    color: white;
    margin-right: 6px;
  }

  .primary:hover {
    background-color: white;
    color: black;
    border-color: black;
    border-width: 1px;
  }

  .text {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 8px;
    box-sizing: border-box;
  }
</style>
