---
layout: post
title: Comment Sorting System
---

Today I'm going to be mentioning ways in implementa comment sorting algo. This will be a multiple part thing first showing really bad methods.

Say we have a comment tree that looks like this for example:

    RootComments: [
      node: {
        comment: 'first',
        votes: '-4',
        children: []
      },
      node: {
        comment: 'Oh wow this is good.',
        votes: '50',
        children: [
          node: {
            comment: 'Yea I can see how this can be helpful.',
            votes: '34',
            children: []
          }
        ]
      },
      node: {
        comment: '....',
        votes: '100',
        children: [
          node: {
            comment: 'This really got 100 upvotes?!',
            votes: '10',
            children: []
          }
        ]
      }
    ]

How might you want to sorts these?

One way is to compare all the comments in each child array. You might want to sort the array by moving branches around based off the immediate child's votes.

E.G. Simplified input with just votes:

    root: [child1 = [votes = 6, child11 = [votes: 46]],
           child2 = [votes = 19,child21 = [votes: -2]
                                child22 = [votes: 73]],
           child3 = [votes = -2]]

After sorting it might end up changing to:

    root: [child2 = [votes = 19,child22 = [votes: 73]
                                child21 = [votes: -2]],
           child1 = [votes = 6, child11 = [votes: 46]],
           child3 = [votes = -2]]

This might work for small arrays, but when they get bigger and bigger this will start slowing down the system.

For each check worst case senerio is going to be n^2, and that times the amount of child checks. You can see this will start getting out of control very soon.

Next post we'll see if we can make this faster!
