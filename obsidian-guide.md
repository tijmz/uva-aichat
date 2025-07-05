
# Introduction
This is a guide for integrating UvA AI Chat with Obsidian, the open source, markdown-based personal knowledge management system. You can learn more about this tool via https://obsidian.md/.

Integrating UvA AI Chat with Obsidian will allow you to run prompts over whole notes or text selections, without sharing these notes with any parties outside of UvA. This can support your work in education or research, as shown by the example prompts in the appendix below.

Before starting this guide, make sure you have:

- A working installation of Obsidian and a vault into which you install the integration
- An API key for UvA AI Chat

# Installing Text Generator
The first thing to do is enable Obsidian to connect to large language models in the first place. For this, head into **Settings -> Community Plugins** and browse for community plugins. The name of the plugin you want is Text Generator, created by Noureddine Haouari. Select and install the plugin and enable it in Obsidian.

Full documentation for Text Generator and its syntax for prompts can be found here: https://github.com/nhaouari/obsidian-textgenerator-plugin. For now, just verify whether you have a new folder called 'text generator' which contains a subfolder with prompts. If that's not the case:

1. Head to **Settings -> Community Plugins**
2. Locate Text Generator in the section **Installed Plugins**
3. Select 'Options' for the Text Generator plugin (the gear icon)
4. Head to **Advanced Settings**
5. Enter a value in the dialog box for **Templates Path**. This is the path where prompts will be stored.

# Adding UvA AI Chat to Text Generator

1. Head to **Settings -> Community Plugins**
2. Locate Text Generator in the section **Installed Plugins**
3. Select 'Options' for the Text Generator plugin (the gear icon)
4. Here, you can add LLM profiles: select the profile 'Custom'
5. Now, we need to add the particulars for UvA AI Chat:

![Image of Text Generator settings](https://github.com/tijmz/uva-aichat/textgen.png))

6. As the Endpoint, use https://ai-research-proxy.azurewebsites.net/v1/chat/completions
7. For API Key, use your personal API key
8. For model, list gpt-35-turbo

That's it! Now you should be good to go.

>[!note] 
>Note that UvA AI Chat offers multiple models and may change the names of existing models. If you wish to use a different model or if you receive a 'MODEL NOT FOUND' error while using the integration with UvA AI Chat, you may need to change the model name. See the section Troubleshooting for how to request the current list of available models.

# Using prompts in Obsidian
If you go to Settings -> Hotkeys in Obsidian, you will see the list of keyboard shortcuts in your current installation. Filter on text generator and you will see an entry for 'Text Generator: Templates: Generate & Insert'. Create a hotkey for this (I myself use CTRL + J, but you can choose whatever you want).

If you now press your chosen hotkey you will see a list of prompts you can use. These correspond to the files in the prompt templates folder (usually **textgenerator > prompts**). If you select them from the popup list, you will run them on (a selection of) your current note.

If you wish to have more details on the prompts, you can simply open the files in the prompt templates folder in Obsidian: each of them is its own Markdown file. You can add your own prompts to the folder by adding new files, but make sure to follow the overall structure of the example prompts.

When just starting, one key thing to consider is whether you wish to run a prompt on the whole note (indicated by the use of the {{content}} placeholder in the prompt) or on the current selection (indicated by the use of the {{selection}} placeholder in the prompt).

# Example prompts

## Education

### Revising learning objectives
If  you have a clear description of your course content as an Obsidian note, you can use this content to revise your course's intended learning objectives (ILOs).

```markdown
---
PromptInfo:
 promptId: reviseILO
 name: 🖊️ Revise ILOs
 description: Select list of existing ILOs and revise them
 author: Vincent Tijms
 tags: writing, education
 version: 0.0.2
---

Take the following list: {{selection}} and edit the items so that each uses a single verb from Bloom's taxonomy, describing student behaviour. Keep language parsimonious and clear. Present the new list as a list of bullet points preceded by the phrase 'After successfully completing this course, the student is able to:' Add the appropriate Bloom level to each objective. Place the resultant text under an h2 heading 'LLM-edited ILOs'.
```

Adding the heading is good practice to make sure you can clearly distinguish UvA AI Chat content from your own notes.

### Generating ILOs
If you have a description of course content and no ILOs, you can also generate draft ILOs. For example, you could use the following prompt:

```markdown
---
PromptInfo:
 promptId: genILO
 name: 🧑‍🏫 Create active learning objectives from course description
 description: Takes course info from note and generates ILOs
 author: Vincent Tijms
 tags: writing, education
 version: 0.0.1
---
Take {{content}} and generate good learning objectives. Note that good learning objectives start with a verb at the desired level of knowledge or skills, using Bloom's taxonomy. Make sure each objective is an outcome. Keep each objective as succinct and clear as possible. Output the new list as a series of bullet points, preceded by the sentence 'After successfully completing this course, the student is able to:' Use an h2 header titled 'LLM-generated learning objectives'.
```

### Choosing assessment forms
If you have a list of ILOs, you can quickly generate ideas for appropriate assessment. For example, you could add this to your list of prompt templates:

```markdown
---
PromptInfo:
 promptId: AssessILOs
 name: 📏 Generate ideas for appropriate assessment
 description: Takes list of ILOs and suggest measurements
 author: Vincent Tijms
 tags: writing, education
 version: 0.0.1
---
{{selection}} contains a list of learning objectives. For each objective, suggest two assessment forms that could measure whether a student has achieved this learning outcomes in a valid, reliable manner. Give one traditional suggestion and one innovative suggestion for each learning objective. Present the suggestions in a table under a h2 header titled 'LLM-generated ideas for assessment'
```
