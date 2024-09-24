



|  **Attribute**  |  **Definition**  |  **Details**  | 
|  --- |  --- |  --- | 
| QType |  | MCQ, FTB (TBD) | 
| Body | type: “json” or “string”, required: true, format: {“key”: “value”} | Body contains the text, graphics, media objects and interactions that describe the question’s content.<ul><li>supports instructions in multiple languages: key is the language code and value is instructions in HTML format in the specified language

</li><li>will be in “string” format (instead of a map) when the instructions are in only one language

</li></ul> | 
| Feedback | type: “json”, required: false, format: {“id1”: {“language_1“: “feedback_html“}, “id2”: “feedback_html“} | Feedback shown to the users after response processing. Feedback is a JSON object in key-value format, keys in the JSON are the identifiers of different feedbacks for the question and values are HTML snippet to be shown to the student. After the response processing, the QuML player renders the feedback HTML mapped to the value that is set to the FEEDBACK outcome variable. Similar to “body” and “instructions”, feedback in different languages can be configured. | 
| Solutions | type: “json” or “list”, required: true, format: {“key”: “value”} | Solutions to the question. Multiple solutions can be configured for a question and each answer can have one or more parts, each part is stored in HTML format. Similar to feedback & hints, solutions in multiple languages can be specified. | 
| ResponseDeclaration | {   “<response_variable_1>”: {         “type“: “one of string, integer, float, boolean, map, uri, points, coordinate“         “cardinality“: “single, multiple, or ordered“,         “correctResponse“: {“value“: “<expected response value>“},         “limits”: {“max & min values, word & character limits, max & min length“},         “hints”: {“key”: “value”},         “mapping”: {“SCORE, Feedback & Hints (if any) for different responses“}   },   “<response_variable_2>: {…} } | Response Declaration should have declaration for every response variable in the question body. Response variables are used to capture responses of the user, these variables are generated as a result of an interaction of user with the question. Optionally, response declaration can have the following details: - Hints: Hints to be shown for this response variable. Hints are shown only if they are allowed in the context where the question is being used. - Correct Response: Correct (or optimal) values for the response variable - Mapping to Score & other outcome variables: Map different values to score so that a response can have more nuances than plain right or wrong, e.g.: a multiple choice question with more than one correct answer can support partial scoring  Response Declaration will be null in case of non-interactive questions. | 
| ResponseProcessing | { “eval”: “custom response processing logic using javascript”,   – or –  “template”: “response processing template“ } | Rules to assign values to outcome variables based on the user’s responses.  There are two ways of configuring response processing: - Question authors can provide custom response processing logic as javascript code for their questions. This logic can use the available library methods to get/set question variables. - Question authors can use/configure one of the provided response processing templates to process the response of the question.Response Processing can be used when a question requires a complex response processing logic (e.g. when a question have template variables). | 
| TemplateDeclaration | {   “<template_variable_1>”: {         “type“: “one of string, integer, float, boolean, map, uri, points, coordinate“         “cardinality“: “single, multiple, or ordered“,         “defaultValue”: <default value for the template variable>,         “processing”: {“randomisation logic using random number generation or random value from a list, regex, or custom processing logic using javascript“}   } } | Template declarations declare variables that are to be used specifically for the purposes of cloning items. They can have their value set at runtime. They are referred to within the question body in order to individualise the clone and possibly also within the responseProcessing rules if the cloning process affects the way the question is scored. Similar to body, instruction, feedback & hints, template variables can have different processing logic for each language. | 
| Interactions | type: “list”, enum: \[“simple-choice”, “multi-choice”, “text”, “single-select”, “multi-select”, “order”, “match”, “upload”, “map”] | List of interactions present in the question.  MVP Scope: “simple-choice”, “multi-choice”, “text”, “single-select”, “multi-select” | 
| ScoringMode | type: “string”, enum: \[“system”, “external”, “offline”, “none”] | <ul><li>system: evaluated and score is generated by the platform (e.g. within the player using the response declaration info).

</li><li>external: evaluation is done by an external system. User responses are submitted to an external system and the external system computes and gives back the score information.

</li><li>offline: evaluation is done offline and score information is uploaded back into the platform.

</li><li>none: question has no evaluation and score is never generated for such questions.

</li></ul>MVP Scope: “system” and “none” | 
| QuMLVersion | type: “string”, required: true | Version of the QuML specification using which the question is created. | 
| TimeLimit | type: “float”, required: false | Hard time limit for the question. User has to provide response within this time limit. | 
| ShowTimer | type: “boolean”, required: false | Show or hide timer when playing this question. | 
| DifficultyLevel | “easy”, “medium”, “hard” |  | 
| BloomsLevel | type: “string”, required: false, enum: \[“remember”, “understand”, “apply”, “analyse”, “evaluate”, “create”] | Cognitive processes involved to answer the question. | 
| Purpose | recall, explore, sense, assess, teach, revise |  | 





*****

[[category.storage-team]] 
[[category.confluence]] 