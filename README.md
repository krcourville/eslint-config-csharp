# eslint-config-csharp

This repository is a JavaScript style guide that includes an ESLint
configuration for C# developers with goals of:

* Guiding and enforcing consistent styles that follow SOLID principles
* Making the context switch between C# and JavaScript a little more
intuitive

## Why use a Style Guide?

1. **code consistency**: makes code easier to review and reason about within
a team
1. **centralized reference**: spend less time debating and getting
team members up-so-speed more time creating profitable solutions.
1. **best practices**: Best practices are derived from hard-earned
 experience and are provided to help developers to avoid common
 pitfalls. JavaScript, in particular, is very
 prone to mis-use as it is often regarded as a secondary language for
 hacking one-off functionality into place.

## TODO

- [ ] Create easlint-config-csharp ESLint module

## <a name="inherits-from"></a>Inherits From

This Style Guide inherits all styles from the following sources minus
[Exceptions](#exceptions) and joined with the
[Additions](#additions) outlined below.

### Airbnb JavaScript Style Guide

[Respository Link](https://github.com/airbnb/javascript)

The Airbnb JavaScript Style Guide **will** make you better
JavaScript programmer.  Plan on 2 hours to read through it all.

**BONUS** To learn even **more**, refer to the
[Resources](https://github.com/airbnb/javascript#resources) session.


## <a name="exceptions"></a>Exceptions

Exceptions and or modifications to the styles outlined in
[Inherits From](#inherits-from).

[Strings 6.1](https://github.com/airbnb/javascript#strings--quotes)
Prefer double quotes over single quotes

> Why?
> C# (and also Java) developers have muscule memory for entering
    strings with double quotes.  Using double quotes makes
    the context switch easier.
    
> Single quotes can still be used
    to avoid escaping. In this case, the single quotes help to point
    out there are special characters in use, similiar to using the
    @ sign with a C# string.
    
> Double quotes follows the JSON spec.

## <a name="additions"></a>Additions

Rules additional to those found in [Inherits From](#inherits-from).

1. Do not use 3rd-party libraries when native functionality is available.

    > Why? Promotes consistency.
    > Makes code more portable by not relying on unnecessary 3rd party
    > libraries.

    ```
    const values = [1, 2, 3];

    // bad
    angular.forEach(values, v => foo(v));
    _.each(values, v => foo(v));
    const mapped = _.map(values, v => foo(v));

    // especially bad (mixed usage)
    _.each(values, v => foo(v));
    const mapped = values.map(values, v => foo(v));

    // good
    values.forEach(v => foo(f));
    const mapped = values.map(v => foo(f));
    ```

2. Limit a single file to 100-300 lines (not including white space)

    > Why? Larger files increase the chance of merge
    conflicts and usually are the sign that
    [SRP](https://en.wikipedia.org/wiki/Single_responsibility_principle)
    is not being applied well.
