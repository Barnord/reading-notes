# Unit Testing and Documentation

## Unit Testing Best Practices

Unit tests test specific, isolated pieces of code

Test names should reflect their purpose.

1. Arrange, Act, Assert - instantiate variables, invoke method, verify response
2. One Assert Per Test Method - Only test one thing at a time
3. Avoid Test Interdedpendence - Tests should run independently of each other, and should be able to pass in that condition.
4. Keep it Short, sweet, and Visible - This seems like a reiteration of the last two points...
5. Recognize Test Setup Pain as a Smell - This bit here makes me wish I actually read this two months ago. If tests are a pain to setup, code better.
6. Add Them to the Build - Make your stuff not launch without passing tests, because you don't want to run broken code.

# Art of the README

## Creators & Consumers

No one knows what your thing does, not even you after enough time.

### Consumers

What to tell them:
1. What is this
2. What does happy path look like
3. How is it used
4. What else is relevant

Don't talk too much tho.

### Creators

Name your thing semanticly, one liners are good.

Give people the name, descreiption, and usage.

How to install.

License.

Do those things in that order, because it's becoming a standard.

Be succinct, reading README's is tedious.

## Best Practices

``` curl https://raw.githubusercontent.com/jehna/readme-best-practices/master/README-default.md > README.md ```

Get that README, then edit it until it works for your program.

[<==Back](README.md)