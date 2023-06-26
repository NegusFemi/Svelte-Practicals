<script>
    import {createEventDispatcher} from "svelte";

    const dispatch = createEventDispatcher();
</script>


<h2>THIS IS A POP UP</h2>
<button on:click={() => dispatch('close')}>CLOSE POPUP</button>

<style>
    button {
        background-color: #29192e;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
      }
    </style>