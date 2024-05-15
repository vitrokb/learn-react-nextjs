Ao utilizar um setState, o React faz uma comparação do DOM com o Virtual DOM, a diferença de estado entre eles que definirá a atualização da tela. Um ponto de atenção é que no código a modificação nem é refletida na linha seguinte, por exemplo:

```jsx
import { useState } from 'react';

export default function HomePage() {
	const [likes, setLikes] = useState(0);

	function handleClick() {
		setLikes(likes + 1);
		// Este console.log não mostrará o que está sendo refletido.
		console.log(likes);
	}

	return (
	    <div>
			<h1>Olá mundo!</h1>
			<button onClick={handleClick}>Like ({likes})</button>
	    </div>
	);
}
```

Segue imagem ilustrando o erro comentado no código acima:

![[erros.png]]

Precisamos ter atenção a esse erro, porque podemos estar enviando uma informação incorreta para uma API, por exemplo, com base no que está sendo renderizado na tela mas que na realidade o dado está inconsistente. Para corrigir este problema, utilizamos um `useEffect` para disparar uma ação quando esse estado for atualizado. Segue exemplo de como o código ficaria:

```jsx
import { useEffect, useState } from 'react';

export default function HomePage() {
	const [likes, setLikes] = useState(0);

	function handleClick() {
		setLikes(likes + 1);
	}

	useEffect(() => {
		console.log('Cliquei no botão, olha quantos likes ->', likes);
	}, [likes]);

	return (
		<div>
			<h1>Olá mundo!</h1>
			<button onClick={handleClick}>Like ({likes})</button>
		</div>
	);
}
```

Segue print de como ficou:

![[acerto.png]]

Note que temos uma ação antes mesmo do clique no botão do `useEffect` , caso não queira que essa ação seja executada na montagem do componente, podemos utilizar uma verificação e dar um curto circuito no Hook.