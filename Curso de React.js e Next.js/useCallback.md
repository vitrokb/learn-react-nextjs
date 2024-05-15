É um memoizador de função, para não recriar toda vez que o estado de um componente atualizar.

Bem parecido com o `useMemo`.

Cuidados ao utilizar o `useCallback`:

- Ao memoizar uma função que seta um estado, utilizar o valor da callback do `useState`, exemplo:
	```
	const incrementCounter = useCallback((num) => {
		 setCounter((c) => c + num);
	}, [])
	```
 Desta forma não temos dependência dentro do `useCallback` e com isso a função não é recriada toda vez que o `counter` for atualizado.

 