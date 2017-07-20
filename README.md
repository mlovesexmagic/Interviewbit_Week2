# Interviewbit_Week2

### Hashing: 2 Sum
```
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return a list of integers
    def twoSum(self, a, b):
        n = len(a)  # size of the array
        sum = []
        for i in range(n - 1):
            for j in range(i + 1, n):
                if (a[i] + a[j]) == b:
                    sum.append([i, j])

        n = len(sum)
        if n == 0:
            return []
        elif n == 1:
            sum[0][0] += 1
            sum[0][1] += 1
            return sum[0]
        else:
            result = [sum[0][0], sum[0][1]]
            for i in range(1, n):
                if (result[1]) > (sum[i][1]):
                    result = [sum[i][0], sum[i][1]]
                elif (result[1]) == (sum[i][1]):
                    if (result[0]) > (sum[i][0]):
                        result = [sum[i][0], sum[i][1]]
        result[0] += 1
        result[1] += 1
        return result

A = [-10, -10, -10]
B = -5
# A = [2,3,6,7,4,11,15,5]
# A = [2,7,11,15]
# B =9
# print(twoSum(A,B))
print(Solution.twoSum(A, B))
```

### Hashing: Colorful Number
```
class Solution:
    # @param A : integer
    # @return an integer
    def colorful(self, A):
        B = str(A)
        sizeB = len(B)
        result = []
        for k in range(sizeB):
            if int(B[k]) in result:
                return 0
            result.append(int(B[k]))

        # result = [int(i) for i in str(A)]
        n = len(result)

        for i in range(0, n):  # from 0 to n-1
            sum = result[i]
            for j in range(i+1, n):
                sum = sum * result[j]
                if sum in result:  # not a colorful number
                    return 0
                result.append(sum)
        return 1

# 3 2 4 5 6 8 20 24 40
# a = 3245
# a =23
a = 99
z = Solution()
print(z.colorful(a))
```
