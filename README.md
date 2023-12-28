# TipTacToe
a0=[' ',0, 1, 2]
a1=[0,'-', '-', '-',]
a2=[1,'-', '-', '-',]
a3=[2,'-', '-', '-',]

saved=[]

def victory(sym):
    if any((a1[1] == a1[2] == a1[3] == sym, a2[1] == a2[2] == a2[3] == sym, a3[1] == a3[2] == a3[3] == sym,
            a1[1] == a2[1] == a3[1] == sym, a1[2] == a2[2] == a3[2] == sym, a1[3] == a2[3] == a3[3] == sym,
            a1[1] == a2[2] == a3[3] == sym, a1[3] == a2[2] == a3[1] == sym,)):
        return True
    return False


def print_maps():
    print(*a0)
    print(*a1)
    print(*a2)
    print(*a3)

def step_maps(s1,s2,sym):
    if s1 == 0: a1[s2+1]=sym
    if s1 == 1: a2[s2 + 1]=sym
    if s1 == 2: a3[s2 + 1]=sym

GR=False
while GR == False:
    if len(saved)==9:
        print('НИЧЬЯ')
        GR=True
        break
    step1, step2 = map(int, input('ход x: ').split())
    while (step1, step2) in saved:
        print('место занято, выберите другое')
        step1, step2 = map(int, input('ход x: ').split())
    if ((step1,step2) not in saved):
        saved.append((step1,step2))
        step_maps(step1,step2,'x')
        print_maps()
        GR = victory('x')
        if GR == True:
            print('х - ВЫИГРАЛ')
            break
    step1, step2 = map(int, input('ход o: ').split())
    while (step1, step2) in saved:
        print('место занято, выберите другое')
        step1, step2 = map(int, input('ход 0: ').split())
    if (step1, step2) not in saved:
        step_maps(step1, step2, 'o')
        print_maps()
        GR = victory('o')
        if GR == True:
            print('о - ВЫИГРАЛ')
            break
