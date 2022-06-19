## GraphQL

#### 이강의에서 배우는 것

* Hasura
* postgraphile

#### 필요조건

* api 설계경험
* nodejs

#### Part

* Graphql vs restAPI
* How?

#### How

* Overfetching: 필요한 데이터외에 데이터들을 받아오는 문제
* Underfetching: 한개의 정보를 얻기 위해 2개이상의 URL을 접근하는 문제

#### 실습

[graphql 실습사이트](https://graphql.org/swapi-graphql?query=%23%20Welcome%20to%20GraphiQL%0A%23%0A%23%20GraphiQL%20is%20an%20in-browser%20tool%20for%20writing%2C%20validating%2C%20and%0A%23%20testing%20GraphQL%20queries.%0A%23%0A%23%20Type%20queries%20into%20this%20side%20of%20the%20screen%2C%20and%20you%20will%20see%20intelligent%0A%23%20typeaheads%20aware%20of%20the%20current%20GraphQL%20type%20schema%20and%20live%20syntax%20and%0A%23%20validation%20errors%20highlighted%20within%20the%20text.%0A%23%0A%23%20GraphQL%20queries%20typically%20start%20with%20a%20%22%7B%22%20character.%20Lines%20that%20start%0A%23%20with%20a%20%23%20are%20ignored.%0A%23%0A%23%20An%20example%20GraphQL%20query%20might%20look%20like%3A%0A%23%0A%23%20%20%20%20%20%7B%0A%23%20%20%20%20%20%20%20field(arg%3A%20%22value%22)%20%7B%0A%23%20%20%20%20%20%20%20%20%20subField%0A%23%20%20%20%20%20%20%20%7D%0A%23%20%20%20%20%20%7D%0A%23%0A%23%20Keyboard%20shortcuts%3A%0A%23%0A%23%20%20Prettify%20Query%3A%20%20Shift-Ctrl-P%20(or%20press%20the%20prettify%20button%20above)%0A%23%0A%23%20%20%20%20%20Merge%20Query%3A%20%20Shift-Ctrl-M%20(or%20press%20the%20merge%20button%20above)%0A%23%0A%23%20%20%20%20%20%20%20Run%20Query%3A%20%20Ctrl-Enter%20(or%20press%20the%20play%20button%20above)%0A%23%0A%23%20%20%20Auto%20Complete%3A%20%20Ctrl-Space%20(or%20just%20start%20typing)%0A%23%0A%0A)

#### Apollo Server

node.js grapAPI 

express -> middleware

```bash
npm init -y
npm i applo-server graphql
npm i nodemon -D
```

```javascript
import { ApolloServer, gql } from "apollo-server";

const typeDefs = gql`
    type Query { // mandantory
        text: String // GET /text와 같다
    }
`;

const server = new ApolloServer({ typeDefs });

server.listen().then(({ url }) => {
  console.log(`Running on {url}`);
});

```

#### Scalar Type

Graphql에 내장된 타입이다. `ID, String, Int, Boolean` 등등

#### Query(GET)

유저가 데이터를 얻을려고 하면 Query

#### Mutation(POST, PUT, DELETE)

GraphQL에 대한 대부분은 데이터 fetching이지만, 서버 측 데이터를 수정할 수 있는 방법이 필요합니다. 서버 측 데이터를 수정하는 모든 작업은 mutation을 통해 보내야 한다는 규칙을 설정하는 것이 유용합니다.

#### Not NUllable Fields

`!`을 Null인지 구분한다. 있으면 필수값으로 처리되어야됌

#### Resolvers

하나의 객체 타입정의와 같은 형태로 구성되어야 됌 데이터를 반환함

#### Resolver Type

Resolver 함수에는 parent(root or source), args, context, info 의 네 가지 인수가 순서대로 전달됩니다.

#### Client

Altair GraphQL Client