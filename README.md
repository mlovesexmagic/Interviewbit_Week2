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


### Linked Lists: Add Two Numbers as ListsBookmark Suggest Edit

```
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    # @param A : head node of linked list
    # @param B : head node of linked list
    # @return the head node in the linked list
    def addTwoNumbers(self, A, B):
        result = ListNode(0)
        temp = result
        carry = 0
        while A or B:
            curVal = carry
            if A:
                curVal = curVal + A.val
                A = A.next
            if B:
                curVal = curVal + B.val
                B = B.next
            carry = curVal / 10
            curVal = curVal % 10
            temp.next = ListNode(curVal)
            temp = temp.next
        if carry == 1:
            temp.next = ListNode(1)
        return result.next



# --- testing ---
node1 = ListNode(9);
node2 = ListNode(9);
node3 = ListNode(1);

node4 = ListNode(1);
# node5 = ListNode(6);
# node6 = ListNode(4);

node1.next = node2;
node2.next = node3;

# node4.next = node5;
# node5.next = node6;

z = Solution()
print(z.addTwoNumbers(node1, node4))
```

### Linked Lists: Palindrome List
```
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution:
    # @param A : head node of linked list
    # @return an integer
    def lPalin(self, A):
        curNode = A
        a = []
        while curNode:
            a.append(curNode.val)
            curNode = curNode.next
        n = len(a)
        for i in range(n // 2):
            if a[i] != a[n-1-i]:
                return 0
        return 1


# --- testing ---
node1 = ListNode(1);
node2 = ListNode(2);
node3 = ListNode(3);
node4 = ListNode(3);
node5 = ListNode(2);
node6 = ListNode(1);
node1.next = node2;
node2.next = node3;
node3.next = node4;
node4.next = node5;
node5.next = node6;

z = Solution()
print(z.lPalin(node1))
```

