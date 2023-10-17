import random
import numpy as np

matrix = np.array([['0' for col in range(6)] for row in range(6)])
matrix_PC = np.array([['0' for col in range(6)] for row in range(6)])
matrix_PC_pul = np.array([['0' for col in range(6)] for row in range(6)])
signal = "■"


#карта PC
def show_PC():
    print(f"  0 1 2 3 4 5")
    for j in range(6):
        row_info = " ".join(matrix_PC[j])
        print(f"{j} {row_info}")
def show_PCpul():
    print(f"  0 1 2 3 4 5")
    for j in range(6):
        row_info = " ".join(matrix_PC_pul[j])
        print(f"{j} {row_info}")

#карта игрока
def show_play():
    print(f"  0 1 2 3 4 5")
    for i in range(6):
        row_info = " ".join(matrix[i])
        print(f"{i} {row_info}")

#разамещение кораблей PC
def place_zero1(matrix_PC, lives):
    random_choice = np.random.randint(2)
    cnt = 0
    while cnt != 1:
        if random_choice == 0:
            row = np.random.randint(5)
            col = np.random.randint(4)
        else:
            row = np.random.randint(4)
            col = np.random.randint(5)

        print(row, col, random_choice)
        if random_choice == 1:
            if all(matrix_PC[row:row+3, col] == '0'):
              if lives == 3:
                matrix_PC[row:row + 3, col] = signal
                cnt += 1
              elif lives == 2:
                matrix_PC[row:row + 2, col] = signal
                cnt += 1
              else:
                matrix_PC[row:row + 1, col] = signal
                cnt += 1
        else:
            if all(matrix_PC[row, col:col+3] == '0'):
              if lives == 3:
                matrix_PC[row, col:col+3] = signal
                cnt += 1
              elif lives == 2:
                matrix_PC[row, col:col+2] = signal
                cnt += 1
              else:
                matrix_PC[row, col:col+1] = signal
                cnt += 1

    return matrix_PC
class ship_pc:
  def __init__(self,name):
    self.name = name
  def ship_board_pc(self,name,ship_health,lives,matrix):
    self.name = name
    self.ship_health = ship_health
    self.lives = lives
    place_zero1(matrix,lives)

#размещение кораблей игрока
class ship:
  def __init__(self,name):
    self.name = name
  def ship_board(self,name,ship_health,lives):
    self.name = name
    self.ship_health = ship_health
    self.lives = lives
    const_row = {}
    const_col = {}
    const = {}
    consta = 0
    while len(set(const)) != lives:
      if len(set(const)) != lives:
        print(f' Разместите корабль {name} ')
        row, col = map(int, input().split())
        if row > 6 or row < 0 or col > 6 or col < 0 or matrix[row][col] == "■":
          print("координаты заняты или находятся вне диапазона")
          continue
          return row, col
        const_row[row] = row
        const_col[col] = col
        if len(set(const_row)) == 1 or len(set(const_col)) == 1:
          consta += 1
          const[consta] = consta
          matrix[row][col] = signal
        else:
          print("Корабль должен быть целым! Выберите соседнюю точку:")
          const_row.popitem()
          const_col.popitem()
          continue
          return row, col
      else:
        matrix[row][col] = ship_health

#Для обнуления карты
def start_new_game():
  a = input("Если хотите очистить доску игрока, введите 99. Если хотите очистить доску PC, введите 88")
  if a == 99:
    matrix = [["0"] * 6 for i in range(6) ]
    print(matrix)
  elif a == 88:
    matrix_PC = [["0"] * 6 for i in range(6) ]
    print(matrix_PC)
  else:
    return matrix, matrix_PC

#выстрелы по карте PC

def pl(play_signal):
     countgamePC = np.count_nonzero(matrix_PC == "Т")
     if countgamePC != 6:
      row, col = map(int, input("         Шмаляй! ").split())
      if matrix_PC [row][col] == "■":
       matrix_PC [row][col] = "Т"
       matrix_PC_pul [row][col] = "Т"
       print("Попал!")
       show_PCpul()
       show_PC()
       return True
      else:
       matrix_PC_pul[row][col] = play_signal
       print("Мимо!")
       show_PCpul()
       return True
     else:
      print("Ты победил!")
#выстрелы по карте игрока
def pl_PC(play_signal):
    countgamePC = np.count_nonzero(matrix_PC == "Т")
    if countgamePC != 6:
     random_choice = np.random.randint(2)
     row = np.random.randint(5 if random_choice == 0 else 4)
     col = np.random.randint(5 if random_choice == 1 else 4)
     if matrix [row][col] == "■":
      matrix [row][col] = "Т"
      print("Противник попал!")
      return True
     else:
      matrix[row][col] = play_signal
      print("Противник промахнулся!")
      return True
    else:
      print("Ты проиграл!")
#проверка
countgame = np.count_nonzero(matrix_PC == "Т")
def Check():
  print(countgame)
  if countgame == 6:
   print("Ты победил!")
   return False
  else: True

#Game
print("Доброе пожаловать в игру морской бой!")
ship1 = ship_pc(name = "long")
ship1.ship_board_pc(name = "long",ship_health = "■",lives = 3, matrix = matrix_PC)
ship2 = ship_pc(name = "shot")
ship2.ship_board_pc(name = "shot",ship_health = "■",lives = 1, matrix = matrix_PC)
ship3 = ship_pc(name = "middle")
ship3.ship_board_pc(name = "middle",ship_health = "■",lives = 2, matrix = matrix_PC)
print("Враг разместил свои корабли!")
print("Размести свои корабли!")
ship1 = ship(name = "long")
ship1.ship_board(name = "long",ship_health = "■",lives = 3)
ship2 = ship(name = "shot")
ship2.ship_board(name = "shot",ship_health = "■",lives = 1)
ship3 = ship(name = "middle")
ship3.ship_board(name = "middle",ship_health = "■",lives = 2)
def game():
  count = 0
  while True:
    count += 1
    if count % 2 == 1:
      if not pl("x") is True:
          break
    else:
      print("Враг стреляет!")
      if not pl_PC("x") is True:
        break
game()
