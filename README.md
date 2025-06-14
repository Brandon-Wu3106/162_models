# Instructions

To run the models, unzip the file to obtain the trained roberta and stylometric models.

Since we exclusively tested on Colab for its GPU, we will provide instructions for running on Colab first as a fail safe in case. 

To begin, if you don't want to change the code in anyway, specifically the file paths, then upload both the roberta folder and stylometric file to MyDrive of your Google Drive. Open a Google Colab file and then open the python notebook.

We were kind of informal in our way of testing, so to test a specific dev dataset, extract and copy the raw url from the desired github data file and change following the url variable definition in the 7th cell of the notebook to the target raw url:

```python
url = "https://raw.githubusercontent.com/skgabriel/cs162-final-dev/refs/heads/main/german_wikipedia.jsonl"
```

Use the top version (uncommented) of the cell for dasasets with both AI and human-labels and use the bottom version(uncomment then comment top version) for datasets with only human labels (native speaker data).

In the final cell of the notebook, there is a line that predicts using an ensemble of the two models. 

```python 
preds,_ = predict_ensemble(texts, roberta_model, stylometric_model, weight_hf=0.3, weight_stylo=0.7)
```

In particular, the last two parameters(weight_hf, weight_stylo) of the function specify by how much you want to weight the roberta model and the stylometric model, respectively.You can test with different weight pairs that sum up to 1. 

If you like you can also change the summary for the output as indicated in the cell to match whatever dataset and weights you chose, but this is just something extra we included for clarity and aesthetic.

After these considerations you can then run all notebooks cells in sequential order.

Testing without Google Colab on a VM or local environment would involve setting the current directory to the unzipped folder name and changing each line that loads a model to the relative path of the model (which should be contained in the folder). Otherwise, the same steps/options from above apply.



