# Stock_Price_Predict_Simple_RNN
模型功能：使用前20天的股票数据预测后5天最高收盘价的涨跌幅区间。
模型分为3部分：数据预处理、模型搭建、模型训练与保存。
数据预处理：该部分获取csv文件中股票的高、开、低、收、成交量数据，然后对每一个数让其除于昨日收盘价做数据归一化、0均值化处理（成交量除外），再用相应数据得到上影线、下影线、
实体相对于昨日收盘价的的波动幅度。再按收盘价计算所属类别并转为one-hot格式。最后将数据转为RNN模型输入数据格式。
模型搭建：使用keras中的SimpleRNN搭建RNN模型。使用训练数据集中后20%数据作为测试集，回调函数使用early_stopping，优化器使用Adam。
模型训练与保存：对mTrain_StockData中的每一个股票行情文件都进行模型训练，对其中在测试集上准确率达到50%的模型进行保存。对数据集上样本数较少但重要性较强的预测涨跌幅达到3个百分点的数据给予更高的权重
