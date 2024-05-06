# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️ <br/>
  Avec une API REST, on défini plusieurs points d'entrées vers notre API en utilisant les méthodes/verbes HTTP.<br/>
  Avec une API GraphQL, nous n'avons plus qu'un seul point d'entrée intelligent (POST /graphql) et l'on va se servir du client d'Apollo pour faire notre demande parmis les méthodes proposées par Apollo serveur. Celui-ci se sert de nos resolverspour faire appel à des query ou des mutations pour récupérer un morceau de donnée précise ou agir sur notre base de données.<br />
  <br />
  Pas de typage en REST, on ne peux pas connaître en avance les données reçues.<br />
  <br/>
- les besoins auxquels répond GraphQL ✔️ <br/> <br />
  GraphQL est un langage de requêtage fortement typé. GraphQL nous permet de faire du "exact" fetching on répond à la contrainte d'overfetching de données en REST en précisant exactement pour chaque besoin quelle donnée l'on souhaite récupérer.
  <br/><br />
- la définition d'un schéma ✔️ <br/><br />
  C'est la description des data auxquelles le client peut accéder via l'API GraphQL. Par exemple le schema d'une entité RecentAd : <br/><br />
  ```
  export type RecentAd = {
  id: number;
  title: string;
  price: number;
  picture: string;
  }
  ```
  <br />
- Query ✔️ <br/><br />
  C'est une requête qui permet de récupérer des données sans les modifier (équivalent GET en API REST) <br/><br />
- Mutation ✔️ <br/><br />
  C'est une requête qui permet de modifier des données (équivalent à du PUT, PATCH, DELETE, POST d'une API REST)
  <br/><br />
- Subscription ❌ <br/><br />
  Pour recevoir des notifications en temps réel
  <br/>

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

<br />
Exemple backend <br />
<br />
``
import { Resolver, Query, Arg, Int } from "type-graphql"
import { Ad } from "../entities/ad"
import { GraphQLError } from "graphql"

@Resolver(Ad)
class AdsResolver {

@Query(() => Ad)
async getAdById(@Arg("adId", () => Int) id: number) {
const ad = await Ad.findOne({
where: { id },
relations: { category: true, tags: true },
});
if (!ad) throw new GraphQLError("not found");
return ad;
}

}

export default AdsResolver

``
<br />
Exemple frontend avec Codegen <br />
<br />

```
import { useGetAdByIdQuery } from "@/graphql/generated/schema";

export type AdDetail = {
id: number;
title: string;
price: number;
picture: string;
};

export default function AdDetails() {
const { adId } = router.query;

const { data } = useGetAdByIdQuery({
variables: { adId: typeof adId === "string" ? parseInt(adId, 10) : 0 },
skip: typeof adId === "undefined",
});

const ad = data?.getAdById;
}
return (
...
)
```

Code généré par codegen sous frontend/src/gql/generated

```
export type GetAdByIdQueryVariables = Exact<{
adId: Scalars['Int'];
}>;

export type GetAdByIdQuery = { **typename?: 'Query', getAdById: { **typename?: 'Ad', id: number, title: string, price: number, picture: string, location: string, owner: string, description: string, category: { \_\_typename?: 'Category', id: number } } };

export function useGetAdByIdQuery(baseOptions: Apollo.QueryHookOptions<GetAdByIdQuery, GetAdByIdQueryVariables>) {
const options = {...defaultOptions, ...baseOptions}
return Apollo.useQuery<GetAdByIdQuery, GetAdByIdQueryVariables>(GetAdByIdDocument, options);
}
```

### Utilisation dans un projet ❌ / ✔️

[lien github](...)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️

```

```

```

```

```

```
