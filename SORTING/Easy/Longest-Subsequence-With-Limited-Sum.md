## [Longest Subsequence With Limited Sum](https://leetcode.com/problems/longest-subsequence-with-limited-sum/)

* **C++**

  * 1
  ```cpp
  class Solution {
  public:
      vector<int> answerQueries(vector<int>& nums, vector<int>& q) {
          int n = nums.size(), m = q.size();
          vector<int> pre_sum;
          sort(nums.begin(), nums.end());
        
          int s = 0;
          for(auto x: nums){
              s += x;
              pre_sum.push_back(s);
          }
        
          vector<int> ans(m, 0);
          for(int i = 0; i < m; i++){
              for(int j = 0; j < n; j++){
                  if(pre_sum[j] <= q[i])
                      ans[i] = j+1;
                  else
                      break;
              }
          }
          return ans;
      }
  };
  ```
  
  * 2
  ```cpp
  class Solution {
  public:
      vector<int> answerQueries(vector<int>& nums, vector<int>& q) {
          vector<int> ans;
          sort(nums.begin(), nums.end());
        
          for(int i = 1; i < nums.size(); i++){
              nums[i] += nums[i-1];
          }
          for(int i = 0; i < q.size(); i++){
              int id = upper_bound(nums.begin(), nums.end(), q[i]) - nums.begin();
              ans.push_back(id);
          }
          return ans;
      }
  };
  ```
 