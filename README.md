# Minimum-operations-to-make-balls-D-times
There is a container with A cyan balls. Alexa will do the following operation as many times as he likes (possibly zero times): Add B cyan balls and C red balls into the container. Alexa's objective is to reach a situation where the number of cyan balls in the container is at most D times the number of red balls in it. 

def min_operations(A, B, C, D):
    def is_possible(guess):
        cyan = A + guess * B
        red = guess * C
        return cyan <= D * red

    left = 0
    right = 10**12 
    result = -1

    while left <= right:
        mid = (left + right) // 2

        if is_possible(mid):
            result = mid
            right = mid - 1
        else:
            left = mid + 1

    return result if result != -1 else -1

A, B, C, D = map(int, input().split())

result = min_operations(A, B, C, D)
print(result)
