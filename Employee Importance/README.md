 Employee Importance
 You have a data structure of employee information, including the employee's unique ID, importance value, and direct subordinates' IDs.
program:

class Solution
{

public:

unordered_map<int,Employee*> mp;

    int dfs(int id)
    
    {
        int s=mp[id]->importance;
        
        for(auto& i:mp[id]->subordinates) s+=dfs(i);
        
        return s;
    }
   
    int getImportance(vector<Employee*> employees, int id)
    
    {
        for(auto& i:employees)mp[i->id]=i;
        
        return dfs(id);
    }
};
