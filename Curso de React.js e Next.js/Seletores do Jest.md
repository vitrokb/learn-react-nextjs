Seletores com prefixo `query` -> São os seletores que caso o elemento especificado não seja encontrado, ele retorna `null` e não levanta um erro. E caso encontre múltiplos elementos ele levanta um erro.

Seletores com prefixo `get` -> São os seletores que retorna um erro caso o elemento não seja encontrado e caso encontre múltiplos elementos.

Seletores com prefixo `find` -> São os seletores que retornam `promisse`  que retornam o elemento encontrado. Caso não encontre o elemento ou ache múltiplos elementos, retornara um erro.

OBS -> Para acessar múltiplos elementos, utilize o `all`, por exemplo, `getAllByText`, `queryAllByText`, `findAllByText`.