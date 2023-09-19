
##   Prepare your data

Begin by examining the new data format needed for the OpenAI fine-tuning endpoints. This format is in JSON lines, comprising a sole "messages" key succeeded by an array of chat message dictionaries—each array symbolizes an individual chat session

    {  "messages":  [  {  "role":  "system",  "content":  "You are an assistant that occasionally misspells words"  },  {  "role":  "user",  "content":  "Tell me a story."  },  {  "role":  "assistant",  "content":  "One day a student went to schoool."  }  ]  }

Put the data to training_data.jsonl . You will need at least 10 rows to fine tuning. If you have less than 10 examples, you may get some error messages like this 

> openai.error.InvalidRequestError: file-2hLJikOruqzRpneyn9GFcCU5 has 5
> example(s), but must have at least 10 examples

## Upload files

-   Make a .env file, contain `OPENAI_API_KEY=sk-XXXXXXXX` as key
-   Install `openai` package and `dotenv` package by running `pip install python-dotenv` and `pip install openai`
-   Run upload_file.py using `python upload_file.py`
-   Get File Id from the console. I broke upload file and training model into 2 files because it will takes few seconds for openai to process the uploaded file. If you run training model too soon, you will get this error message : 

> openai.error.InvalidRequestError: File 'file-B43vrZBqDHJsosrTpV0wBVlG'
> is still being processed and is not ready to be used for fine-tuning.
> Please try again later.

##   Create a fine-tuning job

-   Replace FILE_ID in trainning_model.py by your file id in the previous step
- Run `python trainning_model.py` to train your model
- It will takes some minutes to finish, after that you will be able to see your new model name in the console 

