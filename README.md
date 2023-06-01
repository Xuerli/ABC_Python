# treat-abc
ABC adaptation for the TREAT project (ABCT). Here Python script abctMain.py is used as the glue language which calls Prolog programmes with all intermediate data stored as files in the file system. 

# Run ABCT 
Jupyter Notebook 6.4.8, Python 3.9.10 and SWI-Prolog version 8.4.1.
Step1. Download all files.\
Step2. Replace the files in the folder 'data' with your own input files. Otherwise, the given example will be used as the input.\
Step3. Run script abctMain.ipynb.


# Input files
Samples of input file are given under the folder 'data', which needs to be replaced by users.

# Output files 
Output files are also stored in folders under 'data'.\
Folder 'original' contains the original input KG.\
Folder 'solution' contains the fully repaired, fault-free, KGs.\
Folder 'archive' contains intermediate KGs.

# Intermediate files (Produced and used by abctMain.py only. Can be ignored by users)
These files store the intermediate data.\
triples.txt: the triples of KG.\
rules.txt:  the rules.

proofs.txt:\
      record all proofs of sufficiencies, insufficiencies and incompatibilities in three lines respectively.\
      Each line is a list of pairs, where the first element is the goal from the preferred structure and the second element is a list of its proofs or evidences.
      in the format of [(Goal1, [Proof1, Proof2...]), (Goal2, []), ....].

repairPlans.txt\
      record all repair plans in lines. Each line is in the format of the following, where TargCls* is a list of clauses to which the repair plan will apply, and ClE is all clauses which constitute the target proof.\
      [faultkind, [(RepairPlan1,[TargCl1]),  (RepairPlan2, [TargCl2])....], ClE].\
      For example:
      ``` 
      [insuff,([expand([+[father,[eid_1],[eid_2]]])],[[+[father,[eid_1],[eid_2]]]]),[[+[father,[eid_1],[eid_2]]]]].
      ```
      
meta.txt\
      record the following feature in lines respectively. Empty list [] cannot be ignored when the feature is an empty list.\
      Heuristics: heuristics to guide ABCT. \
      ProtectList: whose items will not be changed by ABCT. \
      TheoryGraph: discribe who predicates/relations are linked with each other.\
      RsBanned: the list of repair plans that are banned and will not be generated as repair solutions by ABCT.\
      RsList: the list of repairs that have been applied to the current KG.\
      RsLen: the length of RsList.

