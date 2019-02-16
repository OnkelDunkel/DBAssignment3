# DB assignment 3

## Part 1

### How many Twitter users are in the database?
    [
        { "$group" : { "_id" : "$user", } },
        { "$count" : "user_count" },
    ]
### Who are the most active Twitter users (top ten)?

    [
        { "$group" : { "_id" : "$user", "tweet_count" : { "$sum" : 1 }}},
        { "$sort" : { "tweet_count" : -1 }},
        { "$limit" : 10 },
    ]

### Who are the five most grumpy (most negative tweets) and the most happy (most positive tweets)?

#### Most grumpy

    [
        { "$group" : { "_id" : "$user", "polarity" : { "$avg" : "$polarity" }}},
        { "$sort" : { "polarity" : 1 }},
        { "$limit" : 5 },
    ]

#### Most happy

    [
        { "$group" : { "_id" : "$user", "polarity" : { "$avg" : "$polarity" }}},
        { "$sort" : { "polarity" : -1 }},
        { "$limit" : 5 },
    ]

### Which Twitter users link the most to other Twitter users? (Provide the top ten.)
    
    [
        { "$project" : { "text" : { "$split" : [ "$text", " " ] }, "user" : "$user" }},
        { "$unwind" : "$text" },
        { "$match" : { "text" : { "$regex" : "@[a-zA-Z]+" }}},
        { "$group" : { "_id" : "$user", "count" : { "$sum" : 1 }}},
        { "$sort" : { "count" : -1 }},
        { "$limit" : 10 },
    ]

### Who is are the most mentioned Twitter users? (Provide the top five.)

    [
        { "$project" : { "text" : { "$split" : [ "$text", " " ] }, "user" : "$user" }},
        { "$unwind" : "$text" },
        { "$match" : { "text" : { "$regex" : "@[a-zA-Z]+" }}},
        { "$group" : { "_id" : "$text", "mentions" : { "$sum" : 1 }}},
        { "$sort" : { "mentions" : -1 }},
        { "$limit" : 5 },
    ]

## Part2



