# What is /r/TranscribersofReddit?

/r/TranscribersOfReddit is a subreddit dedicated to the curation and support of transcribing content posted to Reddit. It is a place for helpful souls to meet, discuss, and have fun putting in a little hard work for the benefit of others who may not be able to read/listen/watch the content otherwise, and to make said content easier to read and understand.

# How does the transcription work and what does this form accomplish?

Each type of post must be transcribed in it's own way. For each type, there is a set template that can be filled out to describe the post. This form simplifies the process by only requiring the data, the formatting itself is generated according to the selected post type.

# How the JSON blob format works

All these formats are based off the formatting guide found at: https://www.reddit.com/r/TranscribersOfReddit/wiki/format

Each `types` corresponds to a post format. The `label` is what will be seen in the drop-down list when selecting which form to fill. 

The `content` is where the actual generated code is going to be derived. Inside `content` is a post `header` which will form the title of the transcription. `elements` contains all subsequent lines that is unique to each `type`. Each `element` is a form input that the user must provide information for.

- `description` is the accompanying text asking for a specific type of information (e.g. `Name of poster:`)
- `type` must be a HTML element. This is placed directly into a `createElement(type)`. Most common will be `input` and `textarea`.
- `prefix` is useful if the element needs to be on a new line, then it can be given a `\n\n`. Any additional text/symbols that must be prefixed to the sentence can be placed here. A good example is bolding text on reddit requires a `**double asterisks**`. In this case the prefix would be `**`.
- `suffix` is the same as prefix.
- `placeholder` is any text that needs to be placed in the `placeholder` attribute.
- `value` is any pre-set text that the input field should contain

# Example of format to JSON

An example of conversion from a format to JSON:

    *Image Transcription:*

    ---

    [*Description of Image.*]

    ---
    
In JSON format:
    
    {
                        "label": "Art and Images without Text",
                        "content": {
                                "header": "*Image Transcription:*",
                                "elements": [
                                        {
                                                "description": "Description of the image: ",
                                                "type": "textarea",
                                                "prefix": "\n\n[*",
                                                "suffix": "*]",
                                                "placeholder": "Description of Image",
                                        }       
                                ]       
                        }       
                },
