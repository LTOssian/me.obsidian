https://youtu.be/C9P2Ntk4-XA?si=CMX6R_uuizOxH-En
https://graphql.org/learn/schema/
## Introduction

GraphQL est un language de Query pour les API et un processus côté serveur pour exécuter ces queries.

On peut créer des services GraphQL en définissant un type qui contient des champs qui sont eux mêmes typés. Ensuite on donne des fonctions à chaque champ des types. 

I.E: le type User
```
type Query {
	me: User
}

type User {
	id: ID!
	name: String!
	email: String!
	age: Int!
	size: Float!
	isAdmin: Boolean!
	friends: [String!]
}
```

Maintenant, nous pouvons créer les fonctions qui retournent les données de chaque champs.
```js
function Query_me(request) {
	return request.auth.user;
}

function User_name(user) {
	return user.getName();
}

// etc...
```

Lorsque le processus graphQL reçois un query:
1. Il le valide en vérifiant que le Query appelle des types qui existent bien
2. Il exécute les fonctions associés aux champs demandé par le query.

I.E: Query le nom de l'utilisateur actuel
```graphql
{
	me {
		name
	}
}
```

Va produire cette réponse
```json
{
	"me": {
		"name": "Louisan T."
	}
}
```

## Queries et Mutations
Comme vu dans [l'introduction](##introduction) les query décrivent le résultat qui sera reçu, ce qui permet d'obtenir exactement ce dont on a besoin. 
### Paramètres
### Aliases
### Fragments

### Mutations
Les mutations sont le type d'opération qui permettent de modifier les données côtés serveur. 
