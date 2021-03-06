从使用最大似然来确定线性回归模型的参数的讨论中，我们知道控制着有效模型的复杂度的基函数的数量，需要根据数据集的大小来确定。向对数似然函数中添加正则项后，可以通过正则系数来控制模型的复杂度。当然，基函数的数量和形式的选择仍然对于确定模型的整体行为十分重要。    

由于最大化似然函数通常会导致过度复杂的模型和过拟问题，所以我们不能简单的通过它来确定具体问题的合适的模型复杂度。如1.3节所说的那样，独立的额外数据可以用来确定模型的复杂度，但是这需要较大的计算量，并且浪费了有价值的数据。因此，我们开始讨论既可以避免最大似然的过拟问题，也可以用训练数据本身自动的确定模型复杂度的线性回归的贝叶斯方法。与之前一样，为了简单起见，只考虑单目标变量$$ t $$的情形。对于多个目标变量情形与3.1.5节一样可以直接推广得到。



