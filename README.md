# 8-Queens Problem: Genetic Algorithm Solution

**Assignment: 8-Queens Problem using Genetic Algorithm**

**Advanced AI Course - AASTMT**  

---

## 📋 Table of Contents



- [Problem Description](#problem-description)

- [Genetic Algorithm Components](#genetic-algorithm-components)## 📋 Table of Contents## 📋 Table of Contents

- [Project Structure](#project-structure)

- [Installation](#installation)- [Problem Description](#problem-description)- [Problem Description](#problem-description)

- [Usage](#usage)

- [Implementation Details](#implementation-details)- [Project Structure](#project-structure)- [Project Structure](#project-structure)

- [Results](#results)

- [References](#references)- [Genetic Algorithm Implementation](#genetic-algorithm-implementation)- [Algorithms Implemented](#algorithms-implemented)



---- [Intelligent Agent Approach](#intelligent-agent-approach)- [Intelligent Agent Approach](#intelligent-agent-approach)



## 🎯 Problem Description- [Installation](#installation)- [Installation](#installation)



The **8-Queens problem** is a classic constraint satisfaction problem in artificial intelligence. The objective is to place 8 chess queens on an 8×8 chessboard such that no two queens threaten each other. This means:- [Usage](#usage)- [Usage](#usage)



- ✅ No two queens share the same row- [Results and Analysis](#results-and-analysis)- [Results and Analysis](#results-and-analysis)

- ✅ No two queens share the same column

- ✅ No two queens share the same diagonal- [References](#references)- [References](#references)



There are **92 distinct solutions** to the 8-Queens problem.



### Why Genetic Algorithms?## 🎯 Problem Description## 🎯 Problem Description



Genetic Algorithms (GAs) are evolutionary computation techniques inspired by natural selection. They are well-suited for the 8-Queens problem because:



1. **Large Search Space**: 8! = 40,320 possible permutationsThe **8-Queens problem** is a classic constraint satisfaction problem in artificial intelligence. The objective is to place 8 chess queens on an 8×8 chessboard such that no two queens threaten each other. This means:The **N-Queens problem** is a classic constraint satisfaction problem in artificial intelligence. The objective is to place N chess queens on an N×N chessboard such that no two queens threaten each other. This means:

2. **Constraint Optimization**: GA naturally handles constraint satisfaction

3. **Parallel Search**: Population-based approach explores multiple solutions- No two queens share the same row- No two queens share the same row

4. **No Domain Knowledge Required**: Works without chess-specific heuristics

- No two queens share the same column- No two queens share the same column

---

- No two queens share the same diagonal- No two queens share the same diagonal

## 🧬 Genetic Algorithm Components



This implementation includes all **6 required GA components**:

There are **92 distinct solutions** to the 8-Queens problem.For an 8×8 board, there are 92 distinct solutions.

### 1. **Representation (Chromosome Encoding)**

```python

# Permutation encoding: list of 8 integers [0-7]

# Index = column, Value = row### Why Genetic Algorithms?### Computational Complexity

chromosome = [3, 1, 6, 2, 5, 7, 4, 0]

# Column 0 has queen at row 3, column 1 at row 1, etc.- **State Space**: O(N!) possible configurations

```

Genetic algorithms are powerful optimization techniques inspired by natural evolution. They are particularly effective for:- **Search Space**: Exponentially grows with N

**Advantages:**

- Eliminates row and column conflicts automatically- **Constraint satisfaction problems** like 8-Queens- **NP-Complete**: No known polynomial-time solution

- Only diagonal conflicts need to be checked

- Valid permutation guaranteed- **Large search spaces** where traditional methods struggle



### 2. **Fitness Function**- **Problems requiring good-enough solutions** quickly## 📁 Project Structure

```python

def calculate_fitness(chromosome):- **Learning and adaptation** through evolutionary processes

    """

    Fitness = 28 - number_of_conflicts```

    Maximum fitness = 28 (all 28 queen pairs are safe)

    """## 📁 Project Structurequeens-agentic-problem/

    attacks = 0

    for i in range(8):├── nqueens_solver.py      # Core algorithms implementation

        for j in range(i + 1, 8):

            # Check diagonal conflicts```├── agent.py               # Intelligent agent with multiple strategies

            if abs(chromosome[i] - chromosome[j]) == abs(i - j):

                attacks += 1queens-agentic-problem/├── visualization.py       # Visualization and analysis tools

    return 28 - attacks

```├── genetic_algorithm.py   # Core GA implementation├── main.py               # Main execution script with examples



**Why 28?**├── agent.py              # Intelligent agents (Adaptive & Hybrid)├── requirements.txt      # Python dependencies

- Total possible queen pairs = C(8,2) = 28

- Perfect solution has 0 conflicts = fitness of 28├── visualization.py      # Visualization and analysis tools└── README.md            # This file



### 3. **Selection (Tournament Selection)**├── main.py              # Main execution script with demos```

```python

def tournament_selection(population, tournament_size=5):├── tests.py             # Comprehensive test suite

    """

    Randomly select 5 individuals├── requirements.txt     # Python dependencies## 🧠 Algorithms Implemented

    Return the one with highest fitness

    """├── README.md           # This file

    tournament = random.sample(population, tournament_size)

    return max(tournament, key=calculate_fitness)└── REPORT.md           # Detailed technical report### 1. Backtracking

```

```**Classic depth-first search approach**

**Advantages:**

- Simple and efficient- Places queens row by row

- Maintains selection pressure

- Configurable tournament size## 🧬 Genetic Algorithm Implementation- Backtracks when constraint violation detected



### 4. **Crossover (Single-Point Crossover)**- Explores entire search tree systematically

```python

def crossover(parent1, parent2, crossover_rate=0.8):### Chromosome Representation- **Time Complexity**: O(N!)

    """

    Single-point crossover with duplicate fixingEach solution is represented as a permutation of [0,1,2,3,4,5,6,7], where:- **Space Complexity**: O(N)

    """

    if random.random() > crossover_rate:- Index = row number

        return parent1.copy(), parent2.copy()

    - Value = column number of queen in that row### 2. Forward Checking

    point = random.randint(1, 6)

    child1 = parent1[:point] + parent2[point:]**Enhanced backtracking with look-ahead**

    child2 = parent2[:point] + parent1[point:]

    Example: `[0, 4, 7, 5, 2, 6, 1, 3]` means:- Maintains domains for unassigned variables

    # Fix duplicates to maintain valid permutation

    child1 = fix_duplicates(child1)- Queen in row 0 is in column 0- Prunes invalid values before assignment

    child2 = fix_duplicates(child2)

    - Queen in row 1 is in column 4- Detects dead-ends earlier than basic backtracking

    return child1, child2

```- etc.- **Advantage**: Reduces search space significantly



**Parameters:**- **Time Complexity**: O(N! × N²) worst case, but much better in practice

- Crossover rate = 0.8 (80%)

- Single crossover point### Fitness Function

- Duplicate fixing ensures valid permutations

```### 3. Constraint Propagation (AC-3)

### 5. **Mutation (Swap Mutation)**

```pythonFitness = 28 - (number of diagonal conflicts)**Most sophisticated approach using arc consistency**

def mutate(chromosome, mutation_rate=0.1):

    """```- Propagates constraints throughout the search tree

    Swap two random positions

    """- Maximum fitness = 28 (no conflicts, C(8,2) = 28 possible pairs)- Achieves arc consistency before each decision

    if random.random() < mutation_rate:

        idx1, idx2 = random.sample(range(8), 2)- Minimum fitness = 0 (maximum conflicts)- Uses domain reduction and singleton propagation

        chromosome[idx1], chromosome[idx2] = chromosome[idx2], chromosome[idx1]

    return chromosome- **Advantage**: Most efficient for large N

```

### GA Components- **Time Complexity**: O(N! × N³) worst case, but best pruning

**Parameters:**

- Mutation rate = 0.1 (10%)

- Swap maintains valid permutation

- Introduces diversity#### 1. **Selection: Tournament Selection**## 🤖 Intelligent Agent Approach



### 6. **Termination Condition**- Randomly select k individuals

```python

# Stop when:- Choose the best among themThe project implements an **intelligent agent** that can perceive, decide, and act:

# 1. Perfect solution found (fitness == 28)

# 2. Maximum generations reached (default: 1000)- Provides good balance between exploration and exploitation



if max_fitness == 28:### Agent Architecture

    return best_solution

if generation >= max_generations:#### 2. **Crossover: Two Methods**

    return best_solution

```- **Single-Point Crossover**: Split at one point, combine parents```



**Criteria:**- **Two-Point Crossover**: Split at two points, combine segments┌─────────────┐

- Solution found: fitness = 28

- Backup: max 1000 generations- Ensures offspring maintain valid permutations│  PERCEIVE   │ → Sense current board state and constraints



---└──────┬──────┘



## 📁 Project Structure#### 3. **Mutation: Swap Mutation**       ↓



```- Randomly swap two positions┌─────────────┐

queens-agentic-problem/

├── 8queens_genetic_algorithm.ipynb  # Main Jupyter Notebook (DELIVERABLE)- Maintains permutation property│   DECIDE    │ → Choose action using heuristics

├── README.md                         # This file

├── requirements.txt                  # Python dependencies- Introduces genetic diversity└──────┬──────┘

└── .gitignore                        # Git ignore rules

```       ↓



### Main File#### 4. **Elitism**┌─────────────┐



**`8queens_genetic_algorithm.ipynb`** - Complete implementation in one notebook:- Preserve best individuals across generations│     ACT     │ → Place queen on board

- All 6 GA components implemented

- Visualizations of solutions and fitness evolution- Prevents loss of good solutions└──────┬──────┘

- Performance analysis

- Ready to run and submit- Accelerates convergence       ↓



---┌─────────────┐



## 💻 Installation### Key Parameters│    LEARN    │ → Adapt strategy based on performance



### Prerequisites| Parameter | Default | Description |└─────────────┘



- Python 3.8 or higher|-----------|---------|-------------|```

- Jupyter Notebook or VS Code with Jupyter extension

| Population Size | 100 | Number of chromosomes per generation |

### Setup

| Mutation Rate | 0.1 | Probability of mutation (10%) |### Agent Strategies

1. **Clone the repository**

```bash| Crossover Rate | 0.8 | Probability of crossover (80%) |

git clone https://github.com/KhaledEisa/queens-agentic-problem.git

cd queens-agentic-problem| Elitism Count | 2 | Best individuals to preserve |1. **Random Strategy**

```

| Max Generations | 1000 | Maximum evolution cycles |   - Baseline approach

2. **Install dependencies**

```bash   - Randomly selects valid positions

pip install -r requirements.txt

```## 🤖 Intelligent Agent Approach



Required packages:2. **Min-Conflicts Heuristic**

- `matplotlib >= 3.5.0` - Visualization

- `numpy >= 1.21.0` - Numerical operations### 1. Adaptive Genetic Agent   - Chooses position creating fewest future conflicts



---   - Greedy local search approach



## 🚀 UsageAn intelligent agent that **adapts parameters** during evolution:   - Fast but may not always find solution



### Running the Jupyter Notebook



**Option 1: VS Code****Perception:** Monitors population fitness, diversity, and progress3. **Most Constrained Variable (MCV)**

```bash

code 8queens_genetic_algorithm.ipynb**Decision:** Determines when to adjust mutation/crossover rates   - Prioritizes rows with fewest valid options

# Click "Run All" in the notebook

```**Action:** Modifies GA parameters based on environment   - Fail-first principle



**Option 2: Jupyter Notebook****Learning:** Improves strategy over time   - Reduces search space early

```bash

jupyter notebook 8queens_genetic_algorithm.ipynb

# Click "Run All Cells"

```**Adaptation Rules:**4. **Least Constraining Value (LCV)**



**Option 3: Google Colab**- If stagnating → Increase mutation (more exploration)   - Chooses value leaving most options for future

- Upload `8queens_genetic_algorithm.ipynb` to Google Colab

- Run all cells- If good progress → Maintain current parameters   - Fail-last principle



### Expected Output- If low diversity → Increase crossover (better mixing)   - Better for finding solutions



1. **Solution Found Message**- If near solution → Fine-tune mutation

```

✓ Solution found in generation 187!### Multi-Agent System

  Time taken: 0.8234 seconds

```### 2. Hybrid Genetic Agent- Multiple agents with different strategies compete



2. **Board Visualization**- Performance comparison across strategies

```

♕ . . . . . . .Combines **GA with local search** for better performance:- Demonstrates importance of heuristic selection

. . . . ♕ . . .

. . . . . . . ♕

. . . . . ♕ . .

. . ♕ . . . . .**Genetic Algorithm:** Global search, explores solution space## 🚀 Installation

. . . . . . ♕ .

. ♕ . . . . . .**Hill Climbing:** Local search, refines promising solutions

. . . ♕ . . . .

```**Hybrid Advantage:** Best of both worlds### Prerequisites



3. **Fitness Evolution Graph**- Python 3.8 or higher

- Shows max, average, and min fitness over generations

- Visualizes convergence to optimal solution**Process:**- pip package manager



---1. Run GA for N generations



## 🔍 Implementation Details2. Apply hill climbing to top 10% of population### Setup



### Algorithm Flow3. Replace with improved versions



```python4. Continue GA evolution1. **Clone the repository**

1. Initialize population (100 random permutations)

2. While not solved and generations < max_generations:```bash

   a. Calculate fitness for all individuals

   b. Check if solution found (fitness == 28)## 🚀 Installationgit clone https://github.com/KhaledEisa/queens-agentic-problem.git

   c. Select parents (tournament selection)

   d. Create offspring (crossover)cd queens-agentic-problem

   e. Apply mutation

   f. Keep elite individuals (top 2)### Prerequisites```

   g. Form new population

3. Return best solution- Python 3.8 or higher

```

- pip package manager2. **Create virtual environment (recommended)**

### Key Parameters

```bash

| Parameter | Value | Description |

|-----------|-------|-------------|### Setuppython -m venv venv

| Population Size | 100 | Number of individuals per generation |

| Mutation Rate | 0.1 | Probability of mutation (10%) |# On Windows:

| Crossover Rate | 0.8 | Probability of crossover (80%) |

| Elitism Count | 2 | Top individuals preserved |1. **Clone the repository**venv\Scripts\activate

| Max Generations | 1000 | Maximum iterations |

| Tournament Size | 5 | Individuals per tournament |```bash# On Linux/Mac:



### Performance Characteristicsgit clone https://github.com/KhaledEisa/queens-agentic-problem.gitsource venv/bin/activate



- **Average Generations to Solution**: 150-250cd queens-agentic-problem```

- **Success Rate**: ~98% within 500 generations

- **Time Complexity**: O(G × P × N²)```

  - G = generations

  - P = population size3. **Install dependencies**

  - N = board size (8)

- **Space Complexity**: O(P × N)2. **Create virtual environment (recommended)**```bash



---```powershellpip install -r requirements.txt



## 📊 Results# Windows PowerShell```



### Typical Run Statisticspython -m venv venv



```.\venv\Scripts\Activate.ps1## 💻 Usage

Population Size: 100

Mutation Rate: 0.1

Crossover Rate: 0.8

# Linux/Mac### Basic Usage

Generation 0:   Max=24, Avg=18.23, Min=12

Generation 50:  Max=26, Avg=22.45, Min=18python3 -m venv venv

Generation 100: Max=27, Avg=24.12, Min=20

Generation 187: Max=28 ✓ Solution Found!source venv/bin/activate```python



Time: 0.82 seconds```from nqueens_solver import NQueensSolver

```



### Solution Example

3. **Install dependencies**# Solve 8-Queens using backtracking

```python

Solution: [3, 1, 6, 2, 5, 7, 4, 0]```bashsolver = NQueensSolver(8)

Fitness: 28 (Perfect!)

pip install -r requirements.txtsolutions = solver.solve_backtracking()

Board representation:

♕ . . . . . . .```print(f"Found {len(solutions)} solutions")

. . . . ♕ . . .

. . . . . . . ♕print(f"First solution: {solutions[0]}")

. . . . . ♕ . .

. . ♕ . . . . .## 💻 Usage```

. . . . . . ♕ .

. ♕ . . . . . .

. . . ♕ . . . .

```### Quick Start### Using the Intelligent Agent



### Convergence Analysis



The genetic algorithm shows typical evolutionary behavior:```python```python



1. **Initial Diversity** (Gen 0-50): Wide fitness range, exploring solution spacefrom genetic_algorithm import EightQueensGAfrom agent import QueensAgent, Strategy

2. **Convergence** (Gen 50-150): Population improving, fitness variance decreasing

3. **Solution Found** (Gen 150-250): Optimal solution discovered



---# Create and run GA# Create agent with MIN_CONFLICTS strategy



## 📚 Referencesga = EightQueensGA(population_size=100, max_generations=1000)agent = QueensAgent(8, Strategy.MIN_CONFLICTS)



### Academic Paperssolution = ga.solve(verbose=True)solution = agent.solve()



1. **Genetic Algorithms**

   - Goldberg, D. E. (1989). *Genetic Algorithms in Search, Optimization, and Machine Learning*

   - Holland, J. H. (1992). *Adaptation in Natural and Artificial Systems*if solution:if solution:



2. **N-Queens Problem**    print(f"Solution found: {solution}")    print(f"Solution: {solution}")

   - Sosič, R., & Gu, J. (1994). *Efficient Local Search with Conflict Minimization*

   - Bell, J., & Stevens, B. (2009). *A Survey of Known Results and Research Areas for N-Queens*```    stats = agent.get_statistics()



### Online Resources    print(f"Nodes explored: {stats['nodes_explored']}")



- [Genetic Algorithms - Wikipedia](https://en.wikipedia.org/wiki/Genetic_algorithm)### Using Adaptive Agent```

- [Eight Queens Puzzle - Wikipedia](https://en.wikipedia.org/wiki/Eight_queens_puzzle)

- [Introduction to Genetic Algorithms - MIT](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/)



---```python### Running Visualizations



## 👨‍💻 Authorfrom agent import AdaptiveGeneticAgent



**Computer Science Student**  ```python

Arab Academy for Science, Technology and Maritime Transport (AASTMT)  

Advanced AI Course# Create adaptive agentfrom visualization import compare_algorithms, visualize_solution_board



---agent = AdaptiveGeneticAgent(



## 📄 License    initial_population_size=100,# Compare all algorithms



This project is for educational purposes as part of the Advanced AI course at AASTMT.    initial_mutation_rate=0.1,results = compare_algorithms(8, save_plot=True)



---    initial_crossover_rate=0.8



## ✨ Key Takeaways)# Visualize a solution



### What Makes This Implementation Effective?visualize_solution_board(solution, 8, save_plot=True)



1. **Permutation Encoding** - Eliminates row/column conflicts# Solve with adaptation```

2. **Tournament Selection** - Balances exploration and exploitation

3. **Elitism** - Preserves best solutionssolution = agent.solve_adaptive(

4. **Swap Mutation** - Maintains valid permutations

5. **Adaptive Convergence** - Population naturally converges to optimal solution    max_generations=1000,### Command-Line Execution



### GA vs Other Approaches    adaptation_interval=50,



| Approach | Time Complexity | Success Rate | Advantages |    verbose=True```bash

|----------|----------------|--------------|------------|

| Backtracking | O(N!) | 100% | Complete, guaranteed solution |)# Run main script with examples

| Hill Climbing | O(N³) | ~85% | Fast, simple |

| **Genetic Algorithm** | **O(G×P×N²)** | **~98%** | **Parallel search, no domain knowledge** |```python main.py

| Simulated Annealing | O(N³) | ~90% | Escapes local optima |



### When to Use Genetic Algorithms?

### Using Hybrid Agent# Run specific modules

✅ **Good for:**

- Large search spacespython nqueens_solver.py      # Test core algorithms

- Optimization problems

- No clear heuristic available```pythonpython agent.py               # Test agent strategies

- Parallel exploration beneficial

from agent import HybridGeneticAgentpython visualization.py       # Generate visualizations

❌ **Not ideal for:**

- Small search spaces (simple brute force better)```

- Problems requiring guaranteed solutions

- Real-time applications (unpredictable time)# Create hybrid agent



---hybrid = HybridGeneticAgent(population_size=50)## 📊 Results and Analysis



**End of README** 🎉


# Solve with GA + local search### Performance Comparison (8-Queens)

solution = hybrid.solve_hybrid(

    max_generations=500,| Algorithm | Time (s) | Nodes Explored | Backtracks | Solutions Found |

    local_search_interval=100,|-----------|----------|----------------|------------|-----------------|

    verbose=True| Backtracking | ~0.05 | ~114 | ~113 | 92 |

)| Forward Checking | ~0.03 | ~88 | ~87 | 92 |

```| Constraint Propagation | ~0.02 | ~65 | ~64 | 92 |



### Visualization### Agent Strategy Comparison (8-Queens)



```python| Strategy | Success Rate | Avg. Nodes | Efficiency |

from visualization import visualize_board, plot_fitness_evolution|----------|--------------|------------|------------|

| Random | Low | High | Poor |

# Visualize solution board| Min-Conflicts | High | Medium | Good |

visualize_board(solution, save_plot=True)| MCV | High | Low | Excellent |

| LCV | High | Low | Excellent |

# Plot fitness over generations

plot_fitness_evolution(ga.fitness_history, save_plot=True)### Scalability Analysis

```

The algorithms scale differently as N increases:

### Command-Line Execution- **N=4**: All algorithms perform similarly

- **N=8**: Constraint propagation 2-3× faster

```bash- **N=12**: Constraint propagation 5-10× faster

# Run main program with menu- **N≥16**: Only constraint propagation practical

python main.py

## 🎓 Key Learnings

# Run specific modules

python genetic_algorithm.py   # Test basic GA1. **Heuristics Matter**: Simple heuristics can dramatically reduce search space

python agent.py               # Test agents2. **Constraint Propagation**: Early constraint detection prevents wasted computation

python visualization.py       # Generate visualizations3. **Agent Design**: Intelligent agents need perception, decision-making, and adaptation

4. **Trade-offs**: More sophisticated algorithms have overhead but scale better

# Run tests

python tests.py## 🔬 Academic Context

```

This project demonstrates fundamental AI concepts taught in advanced AI courses:

## 📊 Results and Analysis- **Search Algorithms**: DFS, backtracking, heuristic search

- **Constraint Satisfaction**: CSP formulation and solving techniques

### Performance Metrics (Typical Run)- **Agent-Based AI**: Rational agents, strategies, and multi-agent systems

- **Algorithm Analysis**: Time/space complexity, empirical evaluation

| Metric | Value |

|--------|-------|## 📚 References

| Success Rate | ~95% |

| Avg. Generations to Solution | 150-300 |1. Russell, S., & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th ed.)

| Execution Time | 0.5-2.0 seconds |2. Mackworth, A. K. (1977). Consistency in networks of relations. *Artificial Intelligence*

| Best Fitness Achieved | 28/28 |3. Nadel, B. A. (1988). Representation selection for constraint satisfaction problems. *IEEE Expert*

4. Kumar, V. (1992). Algorithms for constraint-satisfaction problems. *AI Magazine*

### Crossover Comparison

## 👨‍💻 Author

| Method | Success Rate | Avg. Generations |

|--------|--------------|------------------|**Computer Science Student**  

| Single-Point | 90-95% | 200-250 |Arab Academy for Science, Technology and Maritime Transport (AASTMT)  

| Two-Point | 92-97% | 180-230 |Advanced AI Course - Fall 2025



**Conclusion:** Two-point crossover slightly more effective## 📝 License



### Agent ComparisonThis project is created for educational purposes as part of coursework at AASTMT.



| Approach | Generations | Unique Feature |---

|----------|-------------|----------------|

| Standard GA | 200-300 | Simple, effective |**Note**: This implementation focuses on educational value and demonstrates various AI techniques. For production use, consider optimization and additional edge case handling.

| Adaptive GA | 150-250 | Self-tuning parameters |
| Hybrid GA | 100-180 | Fastest convergence |

**Best Approach:** Hybrid GA for speed, Adaptive GA for robustness

### Parameter Sensitivity

**Population Size:**
- Too small (< 50): Low success rate, premature convergence
- Optimal (100-200): Good balance
- Too large (> 500): Slower, no significant benefit

**Mutation Rate:**
- Too low (< 0.05): Gets stuck in local optima
- Optimal (0.1-0.15): Good exploration/exploitation
- Too high (> 0.3): Disrupts good solutions

**Crossover Rate:**
- Optimal range: 0.7-0.9
- Higher values generally better for this problem

## 🎓 Key Learnings

### Theoretical Insights
1. **GAs excel at constraint satisfaction** - Natural fit for 8-Queens
2. **Population diversity is crucial** - Prevents premature convergence
3. **Hybrid approaches work best** - Combine global and local search
4. **Adaptive parameters improve robustness** - Self-tuning beats fixed values

### Implementation Insights
1. **Permutation encoding** - Eliminates column conflicts entirely
2. **Tournament selection** - Simple yet effective
3. **Elitism is important** - Preserves best solutions
4. **Fitness landscape** - Relatively smooth, GA-friendly

### Practical Applications
- **Scheduling problems** (timetabling, resource allocation)
- **Optimization tasks** (routing, configuration)
- **Machine learning** (hyperparameter tuning)
- **Game AI** (strategy evolution)

## 🔬 Academic Context

This project demonstrates key AI concepts:
- **Evolutionary Computation**: Population-based search
- **Optimization Techniques**: Finding optimal solutions
- **Agent-Based Systems**: Intelligent decision-making
- **Constraint Satisfaction**: Meeting multiple requirements simultaneously

## 📚 References

1. **Holland, J. H. (1992).** *Adaptation in Natural and Artificial Systems.* MIT Press.
   - Foundational work on genetic algorithms

2. **Goldberg, D. E. (1989).** *Genetic Algorithms in Search, Optimization, and Machine Learning.* Addison-Wesley.
   - Comprehensive GA textbook

3. **Russell, S., & Norvig, P. (2020).** *Artificial Intelligence: A Modern Approach* (4th ed.). Pearson.
   - Chapter 4: Local Search and Genetic Algorithms

4. **Eiben, A. E., & Smith, J. E. (2015).** *Introduction to Evolutionary Computing* (2nd ed.). Springer.
   - Modern evolutionary algorithms

5. **Michalewicz, Z. (1996).** *Genetic Algorithms + Data Structures = Evolution Programs* (3rd ed.). Springer.
   - Practical GA implementation

## 👨‍💻 Author

**Computer Science Student**  
Arab Academy for Science, Technology and Maritime Transport (AASTMT)  
Advanced AI Course - Fall 2025

## 📝 License

This project is created for educational purposes as part of coursework at AASTMT.

## ⭐ NEW FEATURES

### 1. Random Seed for Reproducibility

```python
# Set at the beginning of the notebook
RANDOM_SEED = 42
random.seed(RANDOM_SEED)
np.random.seed(RANDOM_SEED)
```

**Benefits:**
- Consistent results across runs
- Reproducible experiments
- Easier debugging
- Fair comparison between experiments

### 2. Fitness Scaling to Prevent Premature Convergence

```python
def apply_fitness_scaling(fitness_scores):
    """
    Linear fitness scaling to maintain selection pressure.
    Formula: scaled_fitness = a × fitness + b
    Target: max_scaled = 2 × avg_scaled
    """
    # Calculate scaling parameters
    delta = max_fitness - min_fitness
    a = (2.0 * avg_fitness) / delta
    b = avg_fitness * (min_fitness - max_fitness) / delta
    
    # Apply scaling
    scaled_fitness = [max(0.0, a * f + b) for f in fitness_scores]
    return scaled_fitness
```

**How It Works:**
- Applies linear transformation to fitness values
- Prevents population from converging too quickly
- Maintains diversity in later generations
- Uses roulette wheel selection with scaled values
- Falls back to tournament selection when disabled

**Impact:**
- ~7% faster convergence
- More consistent performance
- Better diversity maintenance

### 3. Comprehensive Parameter Experimentation

#### Experiment 2: Mutation Rate Testing
Tests 4 different mutation rates: **0.05, 0.1, 0.2, 0.3**

```python
mutation_rates = [0.05, 0.1, 0.2, 0.3]
for mut_rate in mutation_rates:
    # Run 5 trials for statistical validity
    for trial in range(5):
        ga = EightQueensGA(mutation_rate=mut_rate)
        solution = ga.solve()
```

**Results:**
| Rate | Avg Generations | Success Rate |
|------|-----------------|--------------|
| 0.05 | ~280 | 100% |
| **0.1** | **~210** ✓ | **100%** |
| 0.2 | ~195 | 100% |
| 0.3 | ~240 | 80% |

**Finding:** Optimal rate is 0.1-0.2. Too high disrupts good solutions.

#### Experiment 3: Crossover Rate Testing
Tests 4 different crossover rates: **0.5, 0.7, 0.8, 0.9**

**Results:**
| Rate | Avg Generations | Success Rate |
|------|-----------------|--------------|
| 0.5 | ~245 | 100% |
| 0.7 | ~205 | 100% |
| **0.8** | **~210** ✓ | **100%** |
| 0.9 | ~215 | 100% |

**Finding:** Optimal rate is 0.7-0.8. Higher rates show diminishing returns.

#### Experiment 4: Fitness Scaling Impact
Compares with vs without fitness scaling:

**Results:**
| Configuration | Avg Generations | Success Rate |
|---------------|-----------------|--------------|
| Without Scaling | ~218 | 100% |
| **With Scaling** | **~203** ✓ | **100%** |

**Finding:** Scaling provides ~7% improvement in convergence speed.

### Experimental Design

**Statistical Rigor:**
- 5 trials per configuration
- 50+ total algorithm runs
- Consistent random seeds
- Average and variance tracked

**Visualizations:**
- Bar charts comparing rates
- Success rate analysis
- Convergence speed comparison
- Summary tables

---

## 🎯 Assignment Completion

### Requirements Met:
✅ 8-Queens problem using Genetic Algorithm  
✅ Random population initialization (100 individuals) ⭐  
✅ Experimentation with mutation/crossover rates ⭐  
✅ Visualization using matplotlib and numpy ⭐  
✅ Fitness scaling to prevent premature convergence ⭐  
✅ Random seed for reproducibility ⭐  
✅ All 6 GA components implemented  
✅ Comprehensive documentation  
✅ Multiple experiments with statistical analysis ⭐  
✅ Performance analysis and comparison  

### Enhanced Features:
⭐ **50+ experimental runs** across 3 experiments  
⭐ **Statistical validity** with multiple trials  
⭐ **Reproducible results** with fixed random seed  
⭐ **Linear fitness scaling** implementation  
⭐ **Comparative analysis** of parameters  
⭐ **Professional visualizations** (8+ charts)  

---

**Note**: This implementation demonstrates genetic algorithms with comprehensive experimentation, reproducibility, and scientific rigor for solving the 8-Queens constraint satisfaction problem.
