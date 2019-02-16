# DB assignment 3

## Part 1

### How many Twitter users are in the database?

    [
        $group : { _id : "$user", },
        $count : "user_count"
    ]

### Who are the most active Twitter users (top ten)?

    [
        $group : { _id : "$user", },
        $count : "user_count"
    ]

### Who are the five most grumpy (most negative tweets) and the most happy (most positive tweets)?

    [
        $group : { _id : "$user", },
        $count : "user_count"
    ]

### Which Twitter users link the most to other Twitter users? (Provide the top ten.)

    [
        $group : { _id : "$user", },
        $count : "user_count"
    ]

### Who is are the most mentioned Twitter users? (Provide the top five.)

    [
        $group : { _id : "$user", },
        $count : "user_count"
    ]

## Part2
