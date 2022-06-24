# Universal Genetic Algorithm

## Project Goals
1. Improve on existing python libraries in the same domain
1. Build a platform that can accomidate a wide variety of genetic algorithms
1. Create tools for the most common and straightforward types of genetic algorithm

## Basic Functionality
Provide a basic template to handle the most common tasks in creating and using a GA, so that users can focus on algorithm creation and utilization. 

## How to Install and Use
### Installation
TODO
### Use
- The BGA project is divided up into the following subsections:
    - selectors
    - genetic_operators
    - generators
    - transcriptors
    - algorithms
    - fitness_functions 
- Each BGA subsection contains a collection of code relating to a specific algorithm or step in that algorithm. 
- The contents of a subsection are divided up by how the implement the general behaviour associated with each subsection. 
- It is possible to implement a simple genetic algorithm without using code from outside of BGA:
    ```
    from bga.selectors.tournament import create_tournament_selector
    from bga.genetic_operators.single_point import create_single_point_crossover
    from bga.genetic_operators.xover_based_mutator import create_xover_based_mutator
    from bga.generators import create_int_list_generator
    # a transcriptor will not be necessary here, see bga/examples/genetic_programming for examples
    from bga.algorithms import create_simple_mutator_algorithm
    from bga.fitness_functions import create_literal_fitness_function

    select = create_tournament_selector(size=3)
    generate = create_int_list_generator(size=4, min=1, max=5)
    cross = create_single_point_crossover(mask_size=4)
    mutate = create_xover_based_mutator(cross, generate)
    fitness_func = create_literal_fitness_function(seq=[1, 2, 3, 4])

    algo = create_simple_mutator_algorithm(
        selector=select,
        generator=generate,
        mutator=mutate,
        fitness_function=fitness_funct
    )

    results = algo(iterations=100)

    print(results["best"])
    ```
- Any of these functions can be replaced by user-defined alternatives. Make sure to navigate to the relevent subsection and follow the guidlines in docs/implementation_guidlines.md (ex. the guidlines for making a selector can be found by following the path uga/selector/docs/implementation_guidlines.md)

## MIT License

Copyright (c) 2022 Emily Ingram

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
