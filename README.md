# LeetCode-Solutions

<hr>

### Two Sum : https://leetcode.com/problems/two-sum/

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n2, i;
        int result[]=new int[2];
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        
        for(i=0;i<nums.length;i++)
        {
            n2 = target - nums[i];
            
            if(map.containsKey(n2))
            {
                result[0]=i;
                result[1]=map.get(n2);
                break;
            }
            else
                map.put(nums[i], i);
        }
        return result;
    }
}
```

<hr>

### Palindrome Number : https://leetcode.com/problems/palindrome-number/

```
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0 || (x!=0 && x%10==0))
            return false;
        
        int n =x, re, rev=0;
        while(n>rev)
        {
            rev = rev*10+n%10;
            n/=10;
        }
        
        return (rev==n || rev/10==n);
        
    }
}
```

<hr>

### Roman to Integer : https://leetcode.com/problems/roman-to-integer/

```
class Solution {
    public int romanToInt(String s) {

    	HashMap<Character,Integer> map = new HashMap<Character,Integer>();
    	map.put('I',1);
    	map.put('V',5);
    	map.put('X',10);
    	map.put('L',50);
    	map.put('C',100);
    	map.put('D',500);
    	map.put('M',1000);

    	int i, l=s.length(), val=0, temp_val=map.get(s.charAt(0));
    	char ch;

    	for(i=0;i<l;i++)
    	{
    		ch = s.charAt(i);
    		if(map.get(ch) <= temp_val)
    			temp_val = map.get(ch);
    		else
    			val-=2*temp_val;
    		val += map.get(ch);
    	}
    	return val;
	}
}
```

<hr>

### Longest Common Prefix : https://leetcode.com/problems/longest-common-prefix/

```
class Solution {
   public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0)
        return "";
    int minLen = Integer.MAX_VALUE;
    for (String str : strs)
        minLen = Math.min(minLen, str.length());
    int low = 1;
    int high = minLen;
    while (low <= high) {
        int middle = (low + high) / 2;
        if (isCommonPrefix(strs, middle))
            low = middle + 1;
        else
            high = middle - 1;
    }
    return strs[0].substring(0, (low + high) / 2);
}

private boolean isCommonPrefix(String[] strs, int len){
    String str1 = strs[0].substring(0,len);
    for (int i = 1; i < strs.length; i++)
        if (!strs[i].startsWith(str1))
            return false;
    return true;
}
}
```

<hr>

### Valid Parentheses : https://leetcode.com/problems/valid-parentheses/

```
import java.util.*;
class Solution {
  public boolean isValid(String str)
  {
    Stack<Character> s = new Stack<Character>();
    HashMap<Character,Character> map = new HashMap<Character,Character>();
    map.put('(',')');
    map.put('{','}');
    map.put('[',']');
    for(char ch:str.toCharArray())
    {
      if(ch=='('||ch=='{'||ch=='[')
        s.push(map.get(ch));
      else
      {
        if(s.isEmpty() || s.pop() != ch)
          return false;
      }
    }
    return s.isEmpty();
  }
}
```

<hr>

### Merge Two Sorted Lists : https://leetcode.com/problems/merge-two-sorted-lists/

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1==NULL) return list2;
        if(list2==NULL) return list1;
        
        ListNode* head = NULL;
        if(list1->val<list2->val)
        {
            head=list1;
            list1=list1->next;
        }
        else
        {
            head=list2;
            list2=list2->next;
        }
        
        ListNode* p=head;        
        while(list1!=NULL && list2!=NULL)
        {
            if(list1->val < list2->val)
            {
                p->next=list1;
                list1=list1->next;
            }
            else
            {
                p->next=list2;
                list2=list2->next;
            }
            p=p->next;
        }
        if(list1==NULL) p->next=list2;
        if(list2==NULL) p->next=list1;
        
        return head;
    }
};
```

<hr>

### Remove Duplicates from Sorted Array : https://leetcode.com/problems/remove-duplicates-from-sorted-array/

```
class Solution {
   public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
}
}
```

<hr>

### Remove Element : https://leetcode.com/problems/remove-element/

```
class Solution {
   public int removeElement(int[] nums, int val) {
    int i = 0;
    int n = nums.length;
    while (i < n) {
        if (nums[i] == val) {
            nums[i] = nums[n - 1];
            // reduce array size by one
            n--;
        } else {
            i++;
        }
    }
    return n;
}
}
```

<hr>

### Implement strStr() : https://leetcode.com/problems/implement-strstr/

```
class Solution {
    public int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);        
    }
}
```

<hr>
