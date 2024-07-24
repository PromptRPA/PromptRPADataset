## PromptRPA Dataset

This is a dataset for the PromptRPA project. The dataset includes 2,500 textual prompts, spanning 100 tasks across 10 application domains, with a total of 533 instructions (i.e. original instructions) and 543 operations (i.e. actual instructions). Each task corresponds to a tutorial.



### Dataset Structure

The root directory contains the following:

- `Tutorial/` - A directory containing subdirectories for each specific tutorial.

- `textual_prompts.xlsx` - An Excel file containing 2,500 textual prompts for 100 different tasks. 

  

#### Tutorial Directory

Each directory in the dataset is named after the tutorial it contains. Each directory contains the following files:

- `tutorial.json`: A JSON file containing the metadata of the tutorial.
- Accessibility node tree of each instructions along with the instruction's screenshot.

Please note that there are 2 tutorials that **cannot be completed using the Accessibility Service API**, which are `在华为手机中开启手写功能的步骤` and `在手机QQ中进入自习室的步骤`. Therefore, these two tutorials do not have the actual_instructions field in the `tutorial.json` file.



##### tutorial.json

The `tutorial.json` file contains the following fields:
- `tutorialName`: The name of the tutorial.
- `tutorialDetail`: The details of the tutorial, can be regarded as the original text.
- `original_instructions`: The original instructions which are results of the Parsing Agent taking the details of the tutorial as input.
- `actual_instructions`: The instructions which are the results of our Grounding Agent. Each instruction contains the following fields:
  - `targetName`: The name of the target node.
  - `type`: The type of the instruction.
  - `para`: The parameters of the instruction.
  - `x`: The x coordinate of the target node.
  - `y`: The y coordinate of the target node.
  - `endX`: The x coordinate of the end of the instruction (only for scroll instructions).
  - `endY`: The y coordinate of the end of the instruction (only for scroll instructions).
  - `storeFolder`: the folder name of the accessibility node tree of the instruction, which locates in the same directory as the `tutorial.json` file. The accessibility node tree is stored in a file named `target_node.json`.
  - `absoluteId`: The absolute id of the target node in the accessibility node tree.
  - `description`: The description of the instruction.
  - `imagePath`: The path of the screenshot of the instruction, which locates in the same directory as the `tutorial.json` file. The screenshot is stored in a file named `[imagePath]` + `.jpg`.
  



### Extra

The data is collected on an Android phone with the following specifications:
- Model: HONOR V20
- Android version: 33
- Screen resolution: 2310 x 1080 pixels
