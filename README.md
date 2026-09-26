# 14._Longest_Common_Prefix
# Write a function to find the longest common prefix string amongst an array of strings.
# If there is no common prefix, return an empty string "".

class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) {
            return "";
        }
        string answer = "";
        for (int j = 0; j < strs[0].size(); j++) {
            char ch = strs[0][j];
            for (int i = 1; i < strs.size(); i++) {
                if (j >= strs[i].size() || strs[i][j] != ch) {
                    return answer;
                }
            }
            answer += ch;
        }
        return answer;
    }
};

# Method II (substr)
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) {
            return "";
        }
        string prefix = strs[0];
        for (int i = 1; i < strs.size(); i++) {
            int j = 0;
            while (j < prefix.size() &&
                   j < strs[i].size() &&
                   prefix[j] == strs[i][j]) {
                j++;
            }
            prefix = prefix.substr(0, j);
        }
        return prefix;
    }
};
