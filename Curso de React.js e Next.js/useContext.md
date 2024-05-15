Cria um contexto para lidar com estados globais na aplicação.

Ao utilizar o contexto dentro de um componente, utilizar como parâmetro a declaração do contexto, por exemplo:

```js
const GlobalContext = React.createContext();

function App () {
	const context = useContext(GlobalContext);

	return (
		<div>{context.text}</div>
	)
}
```
