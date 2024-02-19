<script setup>

</script>


<template>
<div>
    <form id="auto-suggest" action="#" method="post">
    <fieldset>
    <input type="text" class="search" name="search" value="Search / Rechercher..." onfocus="if(this.value=='Search / Rechercher...')this.value=''" onblur="if(this.value=='')this.value='Search / Rechercher...'" autocomplete="off"/>
    </fieldset>
</form>
</div>
</template>