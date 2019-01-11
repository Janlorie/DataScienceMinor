### Classification Tooling to classify faster

![Gif](../Resources/Images/sentence-classification.gif)

After we decided to change from a binary classifier to a multiclass classifier. 
I decided to make a tool to make this process faster and easier to check. 

The tool imports all thee pre-made sentences. 
Displays 9 sentences on the screen where the middle one, is the current sentence. 
The tool waits for a classification (1, 2 , 3 or 4) and appends this sentence with 
classification to the classified sentences file. After that it gets the next sentence and so on. 
On restarting the tool, it begins where you left off.

Below a few code examples: 

### The importing
The importing is done by the Importer from our project. 

```python 
def import_classified_sentences(classified_file):
    reader = csv.reader(
        open('{0}/result/{1}'.format(Path().absolute(), classified_file), mode='r'))
    sentences = list()
    for index, row in enumerate(reader):
        if index == 0:
            continue
        score, sentence = row
        sentences.append({'score': score, 'sentence': sentence})
    return sentences
```

### The displaying
The displaying is done with the Tkinter package. This provides a rather simple way of 
displaying text as well as others but they weren't necessary for this tool. 

First, the sentences are imported. and the starting index is retrieved. The startup function is called. It sets up a root class, for this root class I 
then bind the keyPress event to a function that handles the keyPress. Then set a 
few attributes and center the window. Append the first sentences to the window and 
start the main Loop. After which the tool waits for a classification input. 

```python
    def start_classification(self):
        root.bind('<KeyPress>', self.key_press)
        root.title('N-gram Classifier')
        root.geometry('1800x350')
        root.configure(background="#F0F0F0")
        print(self.starting_index, 'Starting')

        for i in range(self.starting_index - 4, self.starting_index):
            label = Label(root, text=all_sentences[i]['sentence'])
            label.configure(font=('Courier', 15))
            label.pack()
            self.labels.append(label)

        self.to_label_ngram = Label(root, text=all_sentences[self.starting_index]['sentence'])
        self.to_label_ngram.configure(font=('Courier', 25), bg="White", wraplength="1800")
        self.to_label_ngram.pack()

        for i in range(self.starting_index, self.starting_index + 4):
            label = Label(root, text=all_sentences[i]['sentence'])
            label.configure(font=('Courier', 15))
            label.pack()
            self.labels.append(label)

        self.center_window(root)
        root.mainloop()
```

On pressing a key, it appends the classification and sentence to the classified file. Then it ups the index, 
removes the sentences from the screen and appends the new ones. 



