# Ruby Cheat Sheet

## Strings
### Shovel Operator (`<<`) vs `+=` for Strings
Shovel operator uses in place modification (it is an alias of concat) and the plus equals operator will create a new string. 
In place operation is about 1.5 times faster than the plus equals operator.

