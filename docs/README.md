## Framework（BasicChecker included）


1.  ASTManager manager:

    1. `FunctionDecl *getFunctionDecl(ASTFunction *F)`：Use ASTFunction（FUnction structure of Framework）to obtain the struture of Clang - FunctionDecl (FD)

    2. `ASTVariable *getASTVariable(VarDecl *VD)`，`VarDecl *getVarDecl(ASTVariable *V)`：transfer between VarDecl and ASTVariable

    4. `std::unique_ptr<CFG> &getCFG(ASTFunction *F)`：Use ASTFunctionto get CFG，similar to `std::unique_ptr<CFG> functionCFG = std::unique_ptr<CFG>(CFG::buildCFG(
      FD, FD->getBody(), &FD->getASTContext(), CFG::BuildOptions()));`

2. CallGraph call_graph：
    
    1. `std::vector<ASTFunction *> &getTopLevelFunctions()`：analyze all high-level functions, i.e., those function that are not called（e.g., main）

    2.  `ASTFunction *getFunction(FunctionDecl *FD) `：Use FD to obtain ASTFunction

    3.  `std::vector<ASTFunction *> &getParents(ASTFunction *F)`, `std::vector<ASTFunction *> &getChildren(ASTFunction *F)`：get the caller and callee of a certain function
3. Config configure: load the config settings。refer to`TemplateChecker::readConfig().`  for further info

## BasicChecker

BasicChecker have different classes that framework provides，which we can use for analyzing. We can also use all its subclasses for analyzing.

