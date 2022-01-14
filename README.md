# Simple Laravel graphql API using Laravel lighthouse

The schema :

```graphql
type Query {
    "Read"
    questions(user_id: String! @eq): [Question]! @all
    answers(question_id: ID! @eq): [Answer]! @all

    "Read One"
    question(id: ID! @eq): Question! @find
    answer(id: ID! @eq): Answer! @find
}

type Mutation {
    "Create"
    createQuestion(user_id: String!, text: String!) : Question @create
    createAnswer(question_id: ID!, text: String!) : Answer @create

    "Update"
    updateQuestion(id: ID!, text: String!) : Question @update
    updateAnswer(id: ID!, text: String!) : Answer @update
    
    "Delete"
    deleteQuestion(id: ID!) : Question @delete
    deleteAnswer(id: ID!) : Answer @delete
}


type Question {
    id: ID!
    user_id: String!
    text: String!
    answers: [Answer!]! @hasMany 
    created_at: DateTime!
    updated_at: DateTime!
}

type Answer {
    id: ID!
    text: String!
    question_id: ID!
    question: Question! @belongsTo
    created_at: DateTime!
    updated_at: DateTime!
}
```