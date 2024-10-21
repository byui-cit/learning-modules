---
title: JSON - Ponder activities.
description: Practice using JSON
date: 2021-10-15

layout: layouts/post.njk
---

## Preparation

It is recommended to review [JSON - Introduction](../prepare1) before you start. You will also need your editor open with some code:

### Javascript

```javascript
// main.js


```

These activities will be most effective if you TRY them first before you look at the solution. And after you do look at the solution...DO NOT copy and paste the code. Read through it, try to understand what it is doing...then go fix your code.

## Activity 1

Hopefully you will not spend a lot of time as a developer hand coding up JSON, but the need shows up often enough that it is worth practicing a bit. In this case we might be developing a recipe app. Ultimately the data for the recipes will be pulled from a server somewhere, but that service is not ready yet and we need to start building out the frontend code. A simple solution would be to ask the developers (who are on a different team) what the data format is going to look like, and then build out some test data in JSON.

The backend team sends you this message:

>We are going to be using something similar to the [Open Recipe format](https://open-recipe-format.readthedocs.io/en/latest/) for the application, but we will be using JSON instead of YAML. Check out this page [Getting started](https://open-recipe-format.readthedocs.io/en/latest/topics/tutorials/walkthrough.html) to see what a common recipe will look like. Oh, don't use the name of the ingredient as the key, just use `"name": "sugar"`
>
>For now we know that a recipe will have a name, description, ingredient list, steps list. That might change later.

Using the documentation above convert this recipe into JSON:

>## Chocolate Chip Cookies
>
> - 1lb butter - softened
> - 1 1/2 C Brown Sugar
> - 1  C white sugar
> - 3 eggs
> - 2 tsp vanilla
> - 1 1/2 tsp Baking soda
> - 1/2 tsp salt
> - 5 C flour (we like 3 C white and 2 C whole wheat)
> - 2 C semi-sweet chocolate chips
> - 1-2 C shredded coconut
>
> 1. Cream the butter and sugar together, then beat in the eggs and vanilla
> 2. Mix in salt, soda and flour
> 3. Add chocolate chips and coconut
> 4. Bake 8-10 minutes at 350 F


1. Create a file called recipes.json
2. Convert the recipe above to JSON format.
3. Validate your file to make sure there are no errors with something like [JSONLint](https://jsonlint.com)

<details>
<summary>Solution 1</summary>

```json
{
    "recipe_name": "Chocolate Chip Cookies",
    "notes": "A classic cookie recipe",
    "ingredients": [
        {
            "name": "butter",
            "amounts": {
                "amount": "1",
                "unit": "lb"
            },
            "notes": "softened"
        },
        {
            "name": "brown sugar",
            "amounts": {
                "amount": "1 1/2",
                "unit": "cups"
            }
        },
        {
            "name": "white sugar",
            "amounts": {
                "amount": "1",
                "unit": "cup"
            }
        },
        {
            "name": "eggs",
            "amounts": {
                "amount": "3",
                "unit": "each"
            }
        },
        {
            "name": "vanilla",
            "amounts": {
                "amount": "2",
                "unit": "tsp"
            }
        },
        {
            "name": "baking soda",
            "amounts": {
                "amount": "1 1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "salt",
            "amounts": {
                "amount": "1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "flour",
            "amounts": {
                "amount": "5",
                "unit": "cups"
            },
            "notes": "we like 3 C white and 2 C whole wheat"
        },
        {
            "name": "semi-sweet chocolate chips",
            "amounts": {
                "amount": "2",
                "unit": "cups"
            }
        },
        {
            "name": "shredded coconut",
            "amounts": {
                "amount": "1-2",
                "unit": "cups"
            }
        }
    ],
    "steps": [
        "Cream the butter and sugar together, then beat in the eggs and vanilla",
        "Mix in salt, soda and flour",
        "Add chocolate chips and coconut",
        "Bake 8-10 minutes at 350 F"
    ]
}
```

</details>

## Activity 2

One recipe is not very interesting. It is very common to send lists of things. Make the changes necessary to your JSON file to have a list of recipes. You can just copy the recipe from part one. Make sure to validate again to make sure we didn't create any errors.

<details>
<summary>Solution 2</summary>

```json
[
  {
    "recipe_name": "Chocolate Chip Cookies",
    "notes": "A classic cookie recipe",
    "ingredients": [
        {
            "name": "butter",
            "amounts": {
                "amount": "1",
                "unit": "lb"
            },
            "notes": "softened"
        },
        {
            "name": "brown sugar",
            "amounts": {
                "amount": "1 1/2",
                "unit": "cups"
            }
        },
        {
            "name": "white sugar",
            "amounts": {
                "amount": "1",
                "unit": "cup"
            }
        },
        {
            "name": "eggs",
            "amounts": {
                "amount": "3",
                "unit": "each"
            }
        },
        {
            "name": "vanilla",
            "amounts": {
                "amount": "2",
                "unit": "tsp"
            }
        },
        {
            "name": "baking soda",
            "amounts": {
                "amount": "1 1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "salt",
            "amounts": {
                "amount": "1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "flour",
            "amounts": {
                "amount": "5",
                "unit": "cups"
            },
            "notes": "we like 3 C white and 2 C whole wheat"
        },
        {
            "name": "semi-sweet chocolate chips",
            "amounts": {
                "amount": "2",
                "unit": "cups"
            }
        },
        {
            "name": "shredded coconut",
            "amounts": {
                "amount": "1-2",
                "unit": "cups"
            }
        }
    ],
    "steps": [
        "Cream the butter and sugar together, then beat in the eggs and vanilla",
        "Mix in salt, soda and flour",
        "Add chocolate chips and coconut",
        "Bake 8-10 minutes at 350 F"
    ]
},
{
    "recipe_name": "Chocolate Chip Cookies",
    "notes": "A classic cookie recipe",
    "ingredients": [
        {
            "name": "butter",
            "amounts": {
                "amount": "1",
                "unit": "lb"
            },
            "notes": "softened"
        },
        {
            "name": "brown sugar",
            "amounts": {
                "amount": "1 1/2",
                "unit": "cups"
            }
        },
        {
            "name": "white sugar",
            "amounts": {
                "amount": "1",
                "unit": "cup"
            }
        },
        {
            "name": "eggs",
            "amounts": {
                "amount": "3",
                "unit": "each"
            }
        },
        {
            "name": "vanilla",
            "amounts": {
                "amount": "2",
                "unit": "tsp"
            }
        },
        {
            "name": "baking soda",
            "amounts": {
                "amount": "1 1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "salt",
            "amounts": {
                "amount": "1/2",
                "unit": "tsp"
            }
        },
        {
            "name": "flour",
            "amounts": {
                "amount": "5",
                "unit": "cups"
            },
            "notes": "we like 3 C white and 2 C whole wheat"
        },
        {
            "name": "semi-sweet chocolate chips",
            "amounts": {
                "amount": "2",
                "unit": "cups"
            }
        },
        {
            "name": "shredded coconut",
            "amounts": {
                "amount": "1-2",
                "unit": "cups"
            }
        }
    ],
    "steps": [
        "Cream the butter and sugar together, then beat in the eggs and vanilla",
        "Mix in salt, soda and flour",
        "Add chocolate chips and coconut",
        "Bake 8-10 minutes at 350 F"
    ]
}
]
```

</details>
