- 👋 Hi, I’m @jaimetse
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!import numpy as np
import random

# List of biotic and abiotic factors
biotic_factors = ["Animals", "Plants", "Bacteria", "Fungi", "Algae", "Protozoa", "Decomposers", "Parasites", "Herbivores", "Predators"]
abiotic_factors = ["Water", "Soil", "Air", "Sunlight", "Temperature", "Humidity", "Minerals", "pH", "Pressure", "Salinity"]

# Combine the words for the word search
all_factors = biotic_factors + abiotic_factors

# Word search grid dimensions
grid_size = 15

# Initialize the word search grid with random letters
grid = np.array([random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ") for _ in range(grid_size**2)]).reshape(grid_size, grid_size)

# Directions for placing words (right, down, diagonal-right-down)
directions = [(0, 1), (1, 0), (1, 1)]

def can_place_word(word, row, col, direction):
    """Check if a word can be placed at the given position with the given direction."""
    dr, dc = direction
    for i in range(len(word)):
        r, c = row + i * dr, col + i * dc
        if r >= grid_size or c >= grid_size or (grid[r, c] != word[i] and grid[r, c] != ''):
            return False
    return True

def place_word(word):
    """Place a word in the grid if possible."""
    word_len = len(word)
    placed = False
    attempts = 0
    while not placed and attempts < 100:
        attempts += 1
        # Random starting point and direction
        row, col = random.randint(0, grid_size-1), random.randint(0, grid_size-1)
        direction = random.choice(directions)
        
        # Check if the word fits
        if can_place_word(word, row, col, direction):
            dr, dc = direction
            for i in range(word_len):
                grid[row + i * dr, col + i * dc] = word[i]
            placed = True

# Place all words in the grid
for word in all_factors:
    place_word(word.upper())

# Convert grid to list of strings for display
word_search_grid = [" ".join(row) for row in grid]
word_search_grid--
jaimetse/jaimetse is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
