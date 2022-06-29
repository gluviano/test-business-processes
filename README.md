# 🤖 Code Guidelines

<aside>
💡 Algunas consideraciones y consensos para escribir los scripts

</aside>

# Tabla de contenido


- [Paradigma](#paradigma)
- [Estructura](#estructura)
- [Variables](#variables)
- [Objetos](#objetos)
- [Arrays](#arrays)
- [Funciones](#funciones)
- [Operadores](#operadores)
- [Comentarios](#comentarios)
- [Sintaxis](#sintaxis)

# Paradigma

1.1 Prioriza el uso de programación funcional sobre escribir código imperativo.

1.2 Usa las funciones de orden superior disponibles del lenguaje.

```jsx
// good
let selectedUser = users.find((user)=>{
	user.selected
})

// also good forEach, filter, map, reduce, every, some, etc.
```

1.3 No uses iteradores. En su lugar, utiliza funciones de orden superior.

```jsx
const numbers = [1, 2, 3, 4, 5];

// bad
let sum = 0;
for (let num of numbers) {
  sum += num;
}
sum === 15;

// good
let sum = 0;
numbers.forEach((num) => {
  sum += num;
});
sum === 15;

// best (use the functional force)
const sum = numbers.reduce((total, num) => total + num, 0);
sum === 15;

// bad
const increasedByOne = [];
for (let i = 0; i < numbers.length; i++) {
  increasedByOne.push(numbers[i] + 1);
}

// good
const increasedByOne = [];
numbers.forEach((num) => {
  increasedByOne.push(num + 1);
});

// best (keeping it functional)
const increasedByOne = numbers.map((num) => num + 1);
```

1.4 Si tienes que escribir tus propias funciones, asegúrate de que sean funciones puras.

```jsx
// bad
const minAge = 18;

let check = function(edad) {
  return edad >= minimo;
};

// good
var check = function(edad) {
  let minAge = 18;
  return age >= minimo;
};
```

# Estructura

1.1 Inicia los scripts colocando todas las sentencias `import` necesarias. Una por línea.

1.2 Coloca en segundo lugar todas las declaraciones de variables y constantes que estarás usando a lo largo del script.

1.3 Finalmente, agrega la lógica del script.

1.4 En caso de que sea necesario que uses funciones definidas por ti, agrégalas al final del script.

```jsx
import groovy...
import inquisitor...

//

const USERS_LIMIT = 12;
let searchInput = '';
let users = [];

//

users.map((user)=>{

	//

})
```

# Variables

1.1 Favorece el uso de `const` y `let`. Usa `var` solo cuando sea necesario.

1.2 Declara e inicializa las referencias en una sola línea.

```jsx
{
	const LAST_NAME = "Hernández";
	let fullName = name + lastName;
}
```

# Objetos

1.1 Usa la sintaxis literal para crear objetos.

```jsx
// bad
const item = new Object();

// good
const item = {};
```

1.2 Usa sintaxis object-shorthand para llenar o asignar tus objetos.

```jsx
// bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

# Arrays

1.1 Usa la sintaxis literal para crear arreglos.

```jsx
// bad
const items = new Array();

// good
const items = [];
```

1.2 Usa saltos de línea después y antes del cierre del arreglo si éste tiene múltiples líneas

```jsx
// bad
const arr = [
  [0, 1], [2, 3], [4, 5],
];

const objectInArray = [{
  id: 1,
}, {
  id: 2,
}];

const numberInArray = [
  1, 2,
];

// good
const arr = [[0, 1], [2, 3], [4, 5]];

const objectInArray = [
  {
    id: 1,
  },
  {
    id: 2,
  },
];

const numberInArray = [
  1,
  2,
];
```

# Funciones

1.1 Usa notación de flecha cuando utilices una función anónima.

```jsx
// bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

# Operadores

1.1 Prioriza el uso de `===` sobre `==` y de `!==` sobre `! =`.

# Comentarios

1.1 Usa `/** … */` para comentarios multilinea.

```jsx
// bad
// make() returns a new element
// based on the passed in tag name
function make(tag) {

  // ...

  return element;
}

// good
/**
 * make() returns a new element
 * based on the passed-in tag name
 */
function make(tag) {

  // ...

  return element;
}
```

1.2 Usa `//` para comentarios de una línea. Usa una sola línea para el comentario. Deja una línea en blanco arriba del comentario a menos que esté arriba del bloque.

```jsx
// bad
const active = true;  // is current tab

// good
// is current tab
const active = true;

// good
function getType() {
  console.log('fetching type...');

  // set the default type to 'no type'
  const type = this.type || 'no type';

  return type;
}

// also good
function getType() {
  // set the default type to 'no type'
  const type = this.type || 'no type';

  return type;
}
```

1.3 Usa comentarios para todas las funciones que declares y para los bloques especialmente complejos

# Sintaxis

1.1 Usa un máximo de 80 caracteres por línea.

1.2 Usa las comillas simples `‘’` para los strings.

```jsx
// bad
const name = "Capt. Janeway";

// good
const name = 'Capt. Janeway';
```

1.3 Termina todas las líneas posibles con `;`

```jsx
// bad
const name = "Capt. Janeway"

// good
const name = 'Capt. Janeway';
```

1.3 Usa una tabulación a dos espacios.

```jsx
// bad
••••const name = "Capt. Janeway"

// good
••const name = 'Capt. Janeway';
```

1.4 Agrega un espacio entre todos los operadores de una línea.

```jsx
// bad
const x=y+5;

// good
const x = y + 5;
```

1.5 Agrega un salto de linea después de un bloque y antes de la siguiente sentencia.

```jsx
// bad
if (foo) {
  return bar;
}
return baz;

// good
if (foo) {
  return bar;
}

return baz;

// bad
const obj = {
  foo() {
  },
  bar() {
  },
};
return obj;

// good
const obj = {
  foo() {
  },

  bar() {
  },
};

return obj;

// bad
const arr = [
  function foo() {
  },
  function bar() {
  },
];
return arr;

// good
const arr = [
  function foo() {
  },

  function bar() {
  },
];

return arr;
```

1.6 Usa una linea por cada declaración que hagas.

```jsx
// bad
const name, foo, desc;

// good
const name;
const foo;
const desc;
```

1.7 Usa nombres cortos y que describan la funcionalidad de tu variable, no su contenido.

```jsx
// bad
let customer = (name, lastName) => {
	let concatenation = `${name} ${lastName}`;
	return concatenation;
}

// good
let customer = (name, lastName) => {
	let fullName = `${name} ${lastName}`;
	return fullName;
}
```

1.8 Usa camelCase para nombrar tus variables e instancias de objetos y funciones.

```jsx

// bad
let fullname = "Capt. Janeway";

// good
let fullName = "Capt. Janeway";

// good
let maskedName = new MaskedPerson();
```

1.9 Usa screaming snake case para nombrar tus constantes.

```jsx
// bad
const timeout = 2000;

// good
const TIMEOUT = 2000;

// good
const LIMIT_REQUESTED = 10;
```
