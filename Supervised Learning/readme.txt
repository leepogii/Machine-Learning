All the experiment are done by using WEKA 3.8.1.

1. Open terminal.
2. Type the folloing commands.

Put desired input between semicolons. "DIR" indicates the system path of the dataset

*DECISION TREE
Pruned: 
	java -cp ./weka.jar weka.classifiers.trees.J48 -C "CONFIDENCE LEVEL" -M 2 "DIR"
Unpruned:
	java -cp ./weka.jarweka.classifiers.trees.J48 -U -M 2 "DIR"

*NEURAL NETWORK 
	java -cp weka.classifiers.functions.MultilayerPerceptron -L "LEARING RATE" -M "MOMENTUM" -N "EPOCHS" -V 0 -S 0 -E 20 -H a

*BOOSTING
Pruned:
	java -cp ./weka.jar weka.classifiers.meta.AdaBoostM1 -P 100 -S 1 -I "NUM ITERATION" -t "DIR" -W weka.classifiers.trees.J48 -- -C "CONFIDENCE LEVEL" -M 2
Unpruned:
	java -cp ./weka.jar weka.classifiers.meta.AdaBoostM1 -P 100 -S 1 -I "NUM ITERATION" -t "DIR" -W weka.classifiers.trees.J48 -- -U -M 2

KNN
	java -cp ./weka.jar weka.classifiers.lazy.IBk -K "KNN" -W 0 -t "DIR" -A "weka.core.neighboursearch.LinearNNSearch -A \"weka.core.EuclideanDistance -R first-last\""

SUPPORT VECTOR MACHINE
Polynomial:
	java -cp ./weka.jar weka.classifiers.functions.SMO -C 1.0 -L 0.001 -P 1.0E-12 -N 0 -V -1 -W 1 -K "weka.classifiers.functions.supportVector.PolyKernel -C 250007 -E "EXPONENT"
RBF:
	java -cp weka.classifiers.functions.SMO -C 1.0 -L 0.001 -P 1.0E-12 -N 0 -V -1 -W 1 -K "weka.classifiers.functions.supportVector.RBFKernel -C 250007 -G "GAMMA"

