---  
share: "true"  
---  
# Reversi Bot Report  
  
## 1. Pruning and Evaluation Function  
  
### Pruning  
  
The Reversi bot uses alpha-beta pruning to minimize redundant computations and enhance performance.  
  
### Evaluation Function  
  
The bot evaluates game states with a weighted scoring mechanism, derived from precomputed data on piece positions.  
  
## 2. Time Spent by Each Lab Partner  
  
### Time Allocation  
  
I spent 5 hours on this project.  
  
## 3. Algorithm Evaluation  
  
### Heuristic Function and Alpha-Beta Pruning  
  
The bot combines heuristic evaluation and alpha-beta pruning for efficient decision-making.  
  
#### Heuristic Function  
  
Used when open squares exceed 5, estimating move desirability based on piece placement and board control.  
  
#### Alpha-Beta Pruning  
  
Deployed when open squares fall below the threshold, allowing deeper exploration of the game tree.  
  
### Performance Analysis  
  
The adaptive approach enhances efficiency and decision quality, enabling effective competition against human or AI opponents.  
  
### Conclusion  
  
The Reversi bot demonstrates adaptability, achieving competitive performance through strategic heuristic evaluation and alpha-beta pruning. Future enhancements may include parameter fine-tuning and advanced search algorithms exploration.  
```python  
import numpy as np  
import random as rand  
from reversi import *  
import json  
  
class ReversiBot:  
    def __init__(self, move_num: int):  
        self.move_num: int = move_num  
        self.cache: dict[int, tuple[int,tuple[int,int]]] = {}  
        self.weight_array: list[list[int]] = [  
            [0.013033485636798686,0.016883921321966974,0.015881851413839326,0.016889900259366306,0.016081547922976936,0.01674341629308273,0.0159811017746682,0.013537510059562174],  
            [0.016845656122611265,0.01656225448988304,0.01751649289881605,0.014967671885481825,0.017570303335410018,0.017220535497549233,0.017276139615363,0.01606600268573868],  
            [0.015878264051399728,0.017761629332188566,0.013230192677236631,0.024329492065352176,0.011930371686622367,0.019026174592146786,0.01730483851487978,0.01686299504106932],  
            [0.017087803087284116,0.015019688640855993,0.024272692160058545,0.0,0.0,0.01185443918165088,0.017636071646802642,0.01608393949793667],  
            [0.016335054868708513,0.017587642253868073,0.012113327171041854,0.0,0.0,0.024422165595041786,0.015193077825436552,0.017218143922589503],  
            [0.016901260240425032,0.017240863884706956,0.019082376603700484,0.011790464551478053,0.024296607909655866,0.013060988748835602,0.017835768155940252,0.016060621642079283],  
            [0.016306953862931663,0.01744594143750396,0.01758106542272881,0.017786740869265752,0.015399949059453358,0.01790512382977248,0.017057310506547536,0.01698795483271531],  
            [0.013874124235144433,0.016149109915589363,0.016970615914257255,0.01634641484976724,0.01725820280316501,0.016112040503713516,0.01718765134185292,0.013156053853484943],  
        ]  
  
    def make_move(self, state) -> tuple[int,int]:  
        state: ReversiGameState = state  
        valid_moves: list[tuple[int,int]] = state.get_valid_moves()  
  
        move = self.minimax(state, 1, valid_moves)[1]  
        for pot_move in valid_moves:  
            if pot_move[0] == move[0] and pot_move[1] == move[1]:  
                return move  
          
        return rand.choice(valid_moves)   
  
    def minimax(self, state, maximizing_player: int, valid_moves: list[tuple[int,int]], alpha=float('-inf'), beta=float('inf')) -> tuple[float, tuple[int,int]]:  
        self.write_dict_to_json(self.cache, "cache.json")  
        print(str(hash(state)))  
        state: ReversiGameState = state  
        state_hash = hash(state)  
        if (len(valid_moves) == 0):  
            raise ValueError("PANIC PANIC PANIC")  
        if self.get_cache_val(state_hash) is not None:  
            # print(f'score: {score}, move: {move}')  
            return self.get_cache_val(state_hash)  
          
        move: tuple[int,int]  
        vals: list[tuple[float, tuple[int,int]]] = []  
  
          
        for move in valid_moves:  
            # print("bbb")  
            state.state_make_move(move)  
            potential_moves: list[tuple[int,int]] = state.get_valid_moves()  
            if len(potential_moves) == 0:  
                p1, p2 = state.get_score()  
                self.cache_val(hash(state), move, p1-p2)  
                # print(f'score: {p1-p2}, move: {move}')  
                return (p1-p2, move)  
              
            val: tuple[int, tuple[int,int]]  
            if state.num_squares_open() > 5:  
                val = (self.heuristic_function(state, maximizing_player), move)  
            else:  
                val = self.minimax(state, maximizing_player, potential_moves, alpha, beta)  
            vals.append(val)  
            state.state_undo_move(move)  
              
            if state.turn == maximizing_player:  
                alpha = max(alpha, val[0])  
                if alpha >= beta:  
                    break  
            else:  
                beta = min(beta, val[0])  
                if beta <= alpha:  
                    break  
          
        score, move = self.get_mini_max_tuple(state.turn == maximizing_player, vals)  
        self.cache_val(state_hash, move, score)  
        # print(f'score: {score}, move: {move}')  
        return (score, move)  
              
    def get_mini_max_tuple(self, is_maximizer: bool, vals: list[tuple[float, tuple[int,int]]]) -> tuple[int, tuple[int,int]]:  
        if is_maximizer: return max(vals)  
        else: return min(vals)  
          
    def heuristic_function(self, state, maximizing_player) -> float:  
        beta = 100.0  
        state: ReversiGameState = state  
        score: float = 0.0  
        for x in range(state.board_dim):  
            for y in range(state.board_dim):  
                if state.board[x][y] == 0:  
                    continue  
                elif state.board[x][y] == maximizing_player:  
                    score += self.weight_array[x][y]  
                else:  
                    score -= self.weight_array[x][y]  
        score *= beta  
        # print(f"heuristic_function: {score}")  
        return score  
      
    def cache_val(self, state_hash: int, move: tuple[int,int], score: float):  
        self.cache[state_hash] = (score, move)  
      
    def get_cache_val(self, state_hash: int) -> tuple[float, tuple[int,int]] | None:  
        return self.cache.get(state_hash, None)  
      
  
    def write_dict_to_json(self, dictionary, filename):  
        with open(filename, 'w') as f:  
            json.dump(dictionary, f, indent=4)  
          
```  
  
  
```python  
import numpy as np  
  
def parse_board(board_string) -> np.ndarray:  
    # Initialize an 8x8 numpy array filled with zeros  
    board = np.zeros((8, 8), dtype=int)  
      
    # Map characters to row and column indices  
    column_map = {'a': 0, 'b': 1, 'c': 2, 'd': 3, 'e': 4, 'f': 5, 'g': 6, 'h': 7}  
      
    # Iterate over characters in the board string  
    for i in range(0, len(board_string), 2):  
        # Extract row and column indices from the move  
        column = column_map[board_string[i]]  
        row = int(board_string[i + 1]) - 1  
          
        # Determine the player based on the character in the board string  
        if i % 4 == 0:  
            player = 1  
        else:  
            player = 2  
          
        # Update the board with the player's move  
        board[row][column] = player  
      
    return board  
  
def calculate_points(board) -> tuple[int,int]:  
    # Count the number of points for player 1 and player 2  
    player1_points = np.count_nonzero(board == 1)  
    player2_points = np.count_nonzero(board == 2)  
      
    return player1_points, player2_points  
      
def update_weights(weights: np.ndarray, board: np.ndarray) -> np.ndarray:  
    player1_points, player2_points = calculate_points(board)  
    score = player1_points - player2_points  
    winner = 1  
    if (score < 0):   
        score *= -1  
        winner = 2  
      
    # Update the weights based on the outcome of the game  
    for i in range(8):  
        for j in range(8):  
            if board[i][j] == winner:  
                weights[i][j] += score  
    return weights  
  
def run(games: list[str], weights: np.ndarray) -> np.ndarray:  
    for game in games:  
        board = parse_board(game)  
        weights = update_weights(weights, board)  
    return weights  
  
  
def read_file_lines(file_path):  
    lines = []  
    with open(file_path, 'r') as file:  
        lines = file.readlines()  
    lines = [val[0:-1] for val in lines]  
    return lines  
  
def run_files(files: list[str]):  
    weights = np.zeros((8, 8,), dtype=int)  
    for file in files:  
        lines = read_file_lines(file)  
        weights = run(lines, weights)  
        print(file)  
    return weights  
def write_array_to_file(array, filename):  
    with open(filename, 'w') as f:  
        f.write("array_data = \n[\n")  
        for row in array:  
            f.write("\t[" + ','.join([str(x) for x in row]) + "],\n")  
        f.write("]")  
  
file_names = []  
start = "C:\\Users\\walte\\Documents\\cs470\\Project 01 - Reversi\\Egaroucid_Transcript\\0000_egaroucid_6_3_0_lv11\\"  
for i in range(200):  
    file_names.append(f"{start}{'{:07d}'.format(i)}.txt")  
  
array_data = [  
	[21799, 28239, 26563, 28249, 26897, 28004, 26729, 22642],  
	[28175, 27701, 29297, 25034, 29387, 28802, 28895, 26871],  
	[26557, 29707, 22128, 40692, 19954, 31822, 28943, 28204],  
	[28580, 25121, 40597,     0,     0, 19827, 29497, 26901],  
	[27321, 29416, 20260,     0,     0, 40847, 25411, 28798],  
	[28268, 28836, 31916, 19720, 40637, 21845, 29831, 26862],  
	[27274, 29179, 29405, 29749, 25757, 29947, 28529, 28413],  
	[23205, 27010, 28384, 27340, 28865, 26948, 28747, 22004],  
]  
  
sum_vals = sum([sum([x for x in arr]) for arr in array_data])  
print(sum_vals)  
new_vals = [[float(x) / float(sum_vals) for x in arr] for arr in array_data]  
# write_array_to_file(run_files(file_names), "output.txt")  
write_array_to_file(new_vals, "output3.txt")  
  
  
```