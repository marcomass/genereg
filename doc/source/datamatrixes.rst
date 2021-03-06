Data Matrixes Construction
============================================
Extracted data are organized in order to let them be used as input for the data analysis, such that you can analyze the single regulation system of each target gene, by identifying the role of its possible regulatory features quantified as for their impact on the target expression, whatever the feature is, e.g. the gene methylation, the expression of a gene in the same gene set or in another gene set and the expression of genes encoding for transcription factors.

An additive approach is adopted, building five different data matrixes for each gene of interest. In this way you can keep track of each gene regulation system step by step, according to the different types of biological features. More specifically, the matrixes are built starting from the gene expression and methylation value of the model gene and gradually incrementing the number of columns, as follows:

	* **Matrix M1** contains the expression of the model gene, its methylation and the expression of the genes belonging to the same gene set as the model gene;
	
	* **Matrix M2** adds the expression of all the candidate regulatory genes of the model gene to M1, avoiding repetitions;
	
	* **Matrix M3** adds the expression of the candidate regulatory genes of all the genes in the model gene set to M2, avoiding repetitions;
	
	* **Matrix M4** adds the expression of the genes belonging to the other gene sets with respect to the considered model gene to matrix M3, avoiding repetitions;
	
	* **Matrix M5** adds the expression of the candidate regulatory genes of all the genes belonging to the other gene sets to matrix M4, avoiding repetitions.


.. image:: images/matrix.png	

|

Here it is the set of fuctions used to build the five data matrixes:

``create_m1()``

	The CREATE_M1 operation builds the first data matrix for each gene of interest, collecting the current gene expression and methylation values, along with the expression values of all the genes in the same gene set. One data matrix for each target gene is created and exported locally in as many Excel files as the considered genes; while the whole set of M1 matrixes is returned as a Python dictionary (dict_model_v1.p), where each target gene (set as key) is associated to a Pandas dataframe containing M1 data of interest (set as value).
	
	**Return:** a Python dictionary
	
	Example::

		import genereg as gr
		m1_dict = gr.DataMatrixes.create_m1()

|

``create_m2()``

	The CREATE_M2 operation builds the second data matrix for each gene of interest, adding to the first matrix data about the expression of candidate regulatory genes of each gene of interest. One data matrix for each target gene is created and exported locally in as many Excel files as the considered genes; while the whole set of M2 matrixes is returned as a Python dictionary (dict_model_v2.p), where each target gene (set as key) is associated to a Pandas dataframe containing M2 data of interest (set as value). 
	
	**Return:** a Python dictionary
	
	Example::

		import genereg as gr
		m2_dict = gr.DataMatrixes.create_m2()

|

``create_m3()``

	The CREATE_M3 operation builds the third data matrix for the analysis for each gene of interest, adding to the second matrix data about the expression of candidate regulatory genes of genes of interest belonging to the same gene set of the model gene. One data matrix for each target gene is created and exported locally in as many Excel files as the considered genes; while the whole set of M3 matrixes is returned as a Python dictionary (dict_model_v3.p), where each target gene (set as key) is associated to a Pandas dataframe containing M3 data of interest (set as value). 
	
	**Return:** a Python dictionary
	
	Example::

		import genereg as gr
		m3_dict = gr.DataMatrixes.create_m3()

|

``create_m4()``

	The CREATE_M4 operation builds the fourth data matrix for the analysis for each gene of interest, adding to the third matrix data about the expression of genes of interest belonging to the other gene sets with respect ot the model gene. One data matrix for each target gene is created and exported locally in as many Excel files as the considered genes; while the whole set of M4 matrixes is returned as a Python dictionary (dict_model_v4.p), where each target gene (set as key) is associated to a Pandas dataframe containing M4 data of interest (set as value). 
	
	**Return:** a Python dictionary
	
	Example::

		import genereg as gr
		m4_dict = gr.DataMatrixes.create_m4()

|

``create_m5()``

	The CREATE_M5 operation builds the fifth data matrix for the analysis for each gene of interest, adding to the fourth matrix data about the expression of candidate regulatory genes of genes of interest belonging to the other gene sets with respect to the model gene.. One data matrix for each target gene is created and exported locally in as many Excel files as the considered genes; while the whole set of M5 matrixes is returned as a Python dictionary (dict_model_v5.p), where each target gene (set as key) is associated to a Pandas dataframe containing M5 data of interest (set as value).
	
	**Return:** a Python dictionary
	
	Example::

		import genereg as gr
		m5_dict = gr.DataMatrixes.create_m5()
