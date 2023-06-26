<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher(); 
    
    function changeColor() {
        dispatch('changeColor', () => { 
        let card = document.querySelector('.card');
        let currentColor = getComputedStyle(card).backgroundColor;
    
        if (currentColor === 'rgb(241, 241, 241)') {
            card.style.backgroundColor = '#e6e6e6';
        } else {
            card.style.backgroundColor = '#f1f1f1';
        }
    })
}
</script>

<div class="card">
    <slot>
    <h2 class="card-title">Beautiful Card</h2>
    <p class="card-description">This is a stunning card created using CSS.</p>
    <button class="card-button" on:click={changeColor}>Change Color</button>
    </slot>
</div>

<style>
.card {
width: 300px;
padding: 20px;
background-color: #f1f1f1;
border-radius: 10px;
box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
margin: 12px auto;
}

.card-title {
color: #333;
font-size: 24px;
margin-bottom: 10px;
}

.card-description {
color: #777;
font-size: 16px;
margin-bottom: 20px;
}

.card-button {
background-color: #4CAF50;
color: #fff;
border: none;
padding: 10px 20px;
border-radius: 5px;
cursor: pointer;
font-size: 16px;
}

.card-button:hover {
background-color: #45a049;
}
</style>

