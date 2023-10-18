<script lang="ts">
  import { SvelteComponentTyped, createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  // Propsの変数を宣言
  let username: string = "Initial User";  // 初期値を設定
  let age: number = 0;  // 仮の初期値

  // Propsの型定義
  interface Props {
    username: string;
    age: number;
  }

  // Eventsの型定義
  interface Events {
    clicked: CustomEvent<{ message: string }>;
  }

  // Slotsの型定義
  interface Slots {
    default: {};
    footer: {};
  }

  export class MyComponent extends SvelteComponentTyped<Props, Events, Slots> {}

  // ボタンがクリックされたときの処理
  function handleClick() {
    username = "Svelte User";  // usernameを更新
    age = 20;  // ageを更新
    dispatch('clicked', { message: 'Hello from MyComponent' });
  }
</script>

<h1>
  Hello, {username}! You are {age} years old.
</h1>
<button on:click={handleClick}>
  Change Name to "Svelte User"
</button>

<slot></slot> <!-- default slot -->
<slot name="footer"></slot> <!-- named slot: footer -->
