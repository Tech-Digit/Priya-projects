# Message App Task Summary

## Oct 1

**LLM call optimization.** Fewer AI calls when loading messages. (Optimize, Optimize 2)
- NewMessageController.php

## Oct 2

**Faster Amazon message loading.** (Amz msg loading optimize)
- NewMessageController.php

## Oct 5

**Dispatch automation test page (first version).** A new page listing shipped orders. (Show shipped orders data, Dispatch automation test view, Dispatch automation test page changes)
- DispatchAutomationController.php, DispatchAutomation.vue (new page)
- Router.js, ChatPage.vue, routes/api.php

## Oct 6

**Switch to OpenAI and LLM call logging.** A provider switch plus a usage and call-log page. (Switch to open ai, Check llm call logs, Llm call optimize, Ai draft llm call optimize, Llm call optimize 2, Llm call optimize 3)
- LlmClient.php, config/llm.php, LlmCallLog.php (model)
- LlmUsageController.php, LlmUsageSettings.vue, Router.js
- NewMessageController.php, DataFetchControllerPriya.php, AmazonCustomerFeedbackController.php

**Message view panel: action buttons.** (Action btns add on view panel)
- Components.js, MessageViewTodo.html, ChatPage.vue

**Shopify "manual move to resolved" check.** (shopify manual move to resolved check)
- NewMessageController.php

## Oct 7

**Root cause LLM call optimization.** (Root cause llm call optimize, Root cause llm call optimize 2)
- NewMessageController.php

**Message template accuracy check.** (Message template accuracy check, Update)
- Template.php, Templates.html, Components.js
- NewMessageController.php, DataFetchControllerPriya.php, ChatPage.vue

## Oct 9

**Dispatch automation: message content and page changes.** (Automation msg content structure change, Modification on automation msg page, Modification on automation msg page 2, Correction)
- DispatchAutomationController.php, DispatchAutomationService.php
- AutomationMessage.php, AutomationRule.php, config/automation.php
- DispatchAutomation.vue, routes/api.php
- NewMessageController.php (Correction)

## Oct 12

**Dispatch automation: send test and view UI.** The send test is the "Send to buyer" flow. (Send test automation, Dispatch view ui change, Update)
- DispatchAutomationController.php, DispatchAutomationService.php, AutomationMessage.php
- DispatchAutomation.vue, config/automation.php, ChatPage.vue
- NewMessageController.php

## Oct 13

**Dispatch automation: cron, command and logs.** (Cron,command add for dispatch automation, Dispatch msg setting logs)
- DispatchAutomationRun.php (new command), Kernel.php
- DispatchAutomationController.php, DispatchAutomationService.php
- DispatchAutomation.vue, routes/api.php

**Customer note view UI change.** (Msg note view ui change, Update)
- MessageViewTodo.html, ChatPage.vue

## Oct 14

**Customer notes.** A notes drawer, and notes can be opened from the chat. (Customer note section add, Customer note view open chat)
- CustomerNotesController.php, CustomerNotesDrawer.vue
- Components.js, MessageViewTodo.html, ChatPage.vue, routes/api.php

**Urgent message flag.** Stop-dispatch and urgent detection. (Urgent msg flag add)
- StopDispatchController.php, StopDispatchService.php, CustomerIntentAnalyser.php
- OrderChange/BeforeShipmentRule.php, ConversationStateResolver.php, MessageRules.php
- Components.js, MessageViewTodo.html, routes/api.php

**Order-change panel (before shipping).** (Order before shipping notification panel)
- OrderChangeController.php, OrderChangeService.php, OrderChangeDrawer.vue
- ChatPage.vue, routes/api.php

**Dispatch auto template restriction.** (Dispatch auto template restriction)
- NewMessageController.php, Templates.html, DispatchAutomation.vue, Components.js, ChatPage.vue

**LLM fallback optimization.** (Fallback llm call optimize)
- LlmClient.php, config/llm.php
- AmazonCustomerFeedbackController.php, DataFetchControllerPriya.php
