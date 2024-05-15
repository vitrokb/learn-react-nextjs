A grosso modo irei escrever sobre o `useEffect` paralelizando com os ciclos de vida do React. São eles: `componentDidMount`, `componentDidUpdate` e `componentWillUnmount`.

## `componentDidMount` -> 

```jsx
useEffect(() => {
	console.log('Componente montado');
	// Com o array de dependências vazio, tudo que estiver dentro
	// do escopo da callback será executado quando o componente
	// for montado.
}, []);
```

## `componentDidUpdate` ->

```jsx
useEffect(() => {
	console.log('Componente atualizado');
	// Sem o array de dependências, esse useEffect será executado
	// toda vez que o componente for atualizado.

	// CUIDADO com os loops infinitos.
});
```

Podemos também utilizar dependências mais pontuais, por exemplo, queremos que toda vez que o contador atualizar, apenas um `console.log` seja chamado.

```jsx
const [contador, setContador] = useState(0);

useEffect(() => {
	console.log('Contador: {contador}');
	// Esse console só será chamado caso a variável contador seja
	// modificada.
	// CUIDADO com os loops infinitos.
}, [contador]);
```

## `componentWillUnmount` ->

```jsx
useEffect(() => {
	// Essa função adiciona um event listener ao h1 dá página.
	document.querySelector('h1').addEventListener('click', eventFn);

	// O que está dentro da função de retorno, será executado quando
	// o componente for desmontado. Nesse caso, irá remover o "lixo"
	// deixado no h1, removendo o event listener de click com a
	// função eventFn.
	// Atenção na sintaxe de callback no return.
	return () => {
		document.querySelector('h1').removeEventListener('click', eventFn);
	}
});
```
