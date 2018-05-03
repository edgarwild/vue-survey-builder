# vue-survey-builder
This is a survey builder component for vue.js applications.

### How to install
You can install the component using `npm i -S vue-survey-builder`

### Demo
You can see the demo [here](http://vue-survey-builder.s3-website-us-east-1.amazonaws.com/#/)

Please look at the souce code of the demo [here](https://github.com/rajeshwarpatlolla/vue-survey-builder-test)

### Steps to use
**Step 1:**
Once you it install, you can import the `SurveyBuilder` as shown below

`import { SurveyBuilder, SurveyBuilderJson } from 'vue-survey-builder';`

**Step 2:**
Then you can use it in your vue component, as shown below

`<SurveyBuilder :options="SurveyBuilderJson" />`

Here `sampleQuestion` can be the json, which is [here](https://github.com/FissionHQ/vue-survey-builder/blob/master/src/survey-builder.json)

This is used to create a new question. We are using this JSON, to build any type of question. Depending on the type of question, only few keys are used in the whole JSON.

**Step 3:**
It emits an event called `add-update-question` with a question object and the type
`this.$root.$emit('add-update-question', question);`

In your component, keep track of this event to capture it
````
mounted() {
  this.$root.$on('add-update-question', question => {
    window.console.log(question);
  });
},
````
When you get the object, you can cross check for the `id`, in the list of questions you have. If the `id` exists, then it means there is an update to the question, if the `id` doesn't exist, then you can directly add the question to the list of questions.
You can refer the sample code in the [demo repository](https://github.com/rajeshwarpatlolla/vue-survey-builder-test/blob/master/src/components/TestSurveyBuilder.vue#L30)

**Step 4:**
You can add your own logic in your component to show the list of question in read only and edit mode. There is a component to show the list of questions, which will be available in the [demo source code](https://github.com/FissionHQ/vue-survey-builder/blob/master/src/QuestionsView.vue). Please use this component called `QuestionsView` in case, you want to show the list of questions added.

You can import it like,

`import { QuestionsView } from 'vue-survey-builder';`

and then use it like,

`<QuestionsView :questions="questionsList" :readOnly="true" />`

- `questions` is a property which takes an array of questions.

- `readOnly` is used to make the whole component editable or non editable, based on the value we pass. It takes true or false.

### Supported Question types
- BOOLEAN
- SINGLE_CHOICE
- MULTI_CHOICE
- SCALE
- NUMBER
- TEXT
- DATE
- TIME

### Keys of the JSON
- **id** : This is a unique field, which will be created dynamically for every qiestion. This field is required for all type of questions.
- **type** : This represents the type of the question. The supported types are mentioned [here](). This field is required for all type of questions.
- **multiSelect** : This represents whether the question is multi select question or not. This is is `false` by default and will be `true` only for `MULTI_CHOICE` question.
- **characterLimited** : It represents the limit for characters, the user can enter. This is used for text type of questions.
- **hasMinMax** : This represents whether the question has any min and max values or not. This will be used by `NUMBER` type of questions only.
- **allowDecimals** : This represents whether we need to allow the decimals or not. This will be used by `NUMBER` type only.
- **sequence** : This represents the sequence of the question. This field will be used by all the question types.
- **minValue** : This represents the min value. This field will be used by `NUMBER` type of questions only.
- **maxValue** : This represents the max value. This field will be used by `NUMBER` type of questions only.
- **labels** : This represents the labels for scale type of question. This field is required for scale type only.
- **dateFormat** : This represents the date format to be shown. This field is required for `DATE` type of questions.
- **timeFormat** : This represents the date format to be shown. This field is required for `TIME` type of questions. 
- **intervals** : This represents the number of intervals used for `SCALE` type of questions.
- **textLimit** : This represents the number character limit for `TEXT` type of questions.
- **units** : This represents the units to be shown. This field will be used for `NUMBER` type of questions.
- **options** : This represents the options of question. This field is used by `SINGLE_CHOICE` and `MULTI_CHOICE` questions.

### Versions
#### 0.1.0
This version is the initial release of this open source project. It has all the required functionalities to build the surveys using vue.js

### To Do
- Support for rating question
- Introduce drag and drop

#### 0.2.0
From this version you can import both `SurveyBuilder` and  `QuestionsView` from `vue-survey-builder`.

### To Do
- Support for rating question
- Introduce drag and drop

### Organisation
[Fission Labs](http://fissionlabs.com/)

### LICENSE
Please read it [here](https://github.com/FissionHQ/vue-survey-builder/blob/master/LICENSE.md)
