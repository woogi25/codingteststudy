def solution(places):
    result = []
    dx = [-1, 1, 0, 0]
    dy = [0, 0, -1, 1]

    def f(i, j, cnt):
        nonlocal good
        if cnt >2 : return
        if -1<i<5 and -1<j<5:
            if graph[i][j] == 'X':
                return

            if cnt != 0 and graph[i][j] == 'P':
                good = 0
                return

            graph[i][j] = 'X'

            for w in range(4):
                ni = i+dx[w]
                nj = j+dy[w]
                f(ni, nj, cnt+1)

    for case in places:
        graph = [list(r) for r in case]
        good = 1
        for i in range(5):
            for j in range(5):
                if graph[i][j]=='P':
                    f(i,j,0)

        result.append(good)
    return result