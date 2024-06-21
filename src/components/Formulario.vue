<script setup>
    const props = defineProps(['resultado', 'filtroTarefa', 'operador1', 'operador2' ])
    
</script>

<template>
    <form prevent>
        <div class="row">
            <div class="col-1">
                <input @change="props.operador1" id="numero-1"
                    class="form-control" type="number" min="0">
            </div>
            <div class="col-1">
                <input @change="props.operador2" id="numero-2"
                    class="form-control" type="number" min="0">
            </div>
            <div class="col-md-2">
                <select @change="props.filtroTarefa" class="form-control">
                    <option value="somar">Somar</option>
                    <option value="subtrair">Subtrair</option>
                    <option value="multiplicar">Multiplicar</option>
                    <option value="dividir">Dividir</option>
                </select>
            </div>
            <div class="col-2">
                <span>RESULTADO: {{ props.resultado }}</span>
            </div>
        </div>
    </form>
</template>