# Tic-Tac-Toe
#Tic-Tac-Toe Game
def sum(a, b, c ):
    return a + b + c

def printBoard(xState, zState):
    for row in range(3):
        for col in range(3):
            index = row * 3 + col
            player = 'X' if xState[index] else ('Z' if zState[index] else index)
            print(player, end=" | " if col < 2 else "\n")
        if row < 2:
            print("--|---|---")

def checkWin(xState, zState):
    wins = [[0, 1, 2], [3, 4, 5], [6, 7, 8], [0, 3, 6], [1, 4, 7], [2, 5, 8], [0, 4, 8], [2, 4, 6]]
    for win in wins:
        if(sum(xState[win[0]], xState[win[1]], xState[win[2]]) == 3):
            printBoard(xState, zState)
            print("X Won the match")
            return 1
        if(sum(zState[win[0]], zState[win[1]], zState[win[2]]) == 3):
            printBoard(xState, zState)
            print("Z Won the match")
            return 0
    return -1
    
if __name__ == "__main__":
    xState = [0, 0, 0, 0, 0, 0, 0, 0, 0]
    zState = [0, 0, 0, 0, 0, 0, 0, 0, 0]
    turn = 1 # 1 for X and 0 for O
    print("Welcome to Tic Tac Toe")
    g=1
    q=[]
    while(g):
        
        printBoard(xState, zState)
        if(turn == 1):
            print("X's Chance")
            value = int(input("Please enter a value: "))
            if value in q:
                turn = 1 - turn
                print('\n')
                print('In valid move play again')
                g-=1
            else:
                q.append(value)
                xState[value] = 1
        else:
            print("Z's Chance")
            value = int(input("Please enter a value: "))
            if value in q:
                turn = 1 - turn
                print('\n')
                print('In valid move play again')
                g-=1
            else:
                q.append(value)
                zState[value] = 1
        cwin = checkWin(xState, zState)
        if(cwin != -1):
            print("Match over")
            break
        g=g+1
        g=g%10
        if g == 0:
            printBoard(xState, zState)
            print('------------------match is draw------------------------')
            print('\n')
        turn = 1 - turn
