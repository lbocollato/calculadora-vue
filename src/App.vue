<script setup>
import { reactive } from 'vue';


const estado = reactive({
	numX: 0,
	numY: 0,
	resultado: '',
	operacao: '',
})

const trocaOp = (evento) => {
	estado.operacao = evento.target.value;
	calcular();
}
const setarNumX = (evento) => {
	estado.numX = evento.target.value;
	calcular();
}
const setarNumY = (evento) => {
	estado.numY = evento.target.value;
	calcular();
}
const calcular = () => {
	let resultado = '';
	let { operacao, numX, numY } = estado;

	switch (operacao) {
		case 'adicao':
			resultado = parseInt(numX) + parseInt(numY);
			break;
		case 'subtracao':
			resultado = parseInt(numX) - parseInt(numY);
			break;
		case 'multiplicacao':
			resultado = parseInt(numX) * parseInt(numY);
			break;
		case 'divisao':
			resultado = parseInt(numX) / parseInt(numY);
			break;
		default:
			resultado = '';
			break;
	}
	estado.resultado = resultado;
}

</script>
<template>
	<div class="container">
		<header>
			<h1>Calculadora</h1>
			<br />
		</header>

		<body>
			<div class="entrada">
				<h2>X</h2>
				<input @keyup="setarNumX" type="number" placeholder="Valor X">
				<h2>Y</h2>
				<input @keyup="setarNumY" type="number" placeholder="Valor Y">

			</div>
			<div class="seletor">
				<h2>Selecione o Operador</h2>
				<select @change="trocaOp">
					<option value=" ">Escolha aqui</option>
					<option value="adicao">+</option>
					<option value="subtracao">-</option>
					<option value="multiplicacao">*</option>
					<option value="divisao">/</option>
				</select>
			</div>
		</body>
		<footer>
			<h2>Resultado</h2>
			<div class="result">{{ estado.resultado }}</div>

		</footer>
	</div>
</template>
<style scoped>
.container {
	background-color: rgb(180, 175, 184);
	border-radius: 10px;

}

header {
	width: 100%;
	display: flex;
	justify-content: center;

}

body {
	width: auto;
	display: flex;
	flex-direction: column;
	justify-content: center;
}

.entrada {
	border: none;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;


}

.entrada input {
	width: 60%;
	padding: 8px;
	margin-bottom: 10px;
	border: 2px solid;
	font-size: 20px;
	text-align: center;
	border-radius: 8px;
}

.entrada h2 {
	width: 100%;
	font-size: 24px;
	font-weight: bold;
	text-align: center;
}

select {
	padding: 5px;
	text-align: center;
	width: 50%;
	font-size: 20px;
	font-weight: bold;
	border: 2px solid #000;
	border-radius: 10px;
}

.seletor {
	padding: 10px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	border: none;
	font-size: 20px;
}

footer {
	font-weight: bolder;
	font-size: 25px;
	border-style: none;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.result {
	font-size: 30px;
	margin-bottom: 10px;
	border: 2px solid #000;
	padding: 10px;
	background-color: rgb(234, 85, 66);
	border-radius: 10px;
}
</style>