---
title: 'How to add a workflow task with configuration screen'
metadata:
    description: 'How to add a workflow task with configuration screen'
    author: 'Joe Bordes'
content:
    items:
        - '@self.children'
    limit: 5
    order:
        by: date
        dir: desc
    pagination: true
    url_taxonomy_filters: true
taxonomy:
    category:
        - development
        - workflow
    tag:
        - addtask
---

There are two types of workflow tasks that can be added to the system: **custom workflow functions** and full blown **workflow tasks**. The difference is the configuration screen. A **custom function** is just a set of instructions and code that do not need any configuration options, it's task is clearly defined and it just needs to be launched on the given event. For example, a routine that relates products and services of an invoice with the account of the invoice is a custom function. This custom function does not need anything more than what it receives to get it's work done, but it could get a little complicated and we could require an option to indicate if we want to have only products and not services related or the reverse, or both. Now that we need to know which elements to relate the custom function needs a configuration screen and must be converted into a **workflow task with configuration screen**.

===

Here we explain how to create the second type of workflows, [for the first type go here](../13.addworkflowfunction).

A **workflow task** needs a name to show in the configuration section, a class that will extend VTTask and do the work, a template to show the configuration options on screen and it will be associated to certain modules and not to others. Finally it may be active or not depending on a certain module being installed or not.

-   **Add new task definition to the application.** This is done by
    inserting a record with the details in the
    *com\_vtiger\_workflow\_tasktypes* table.
    -   **tasktypename**: internal name of the task
    -   **label**: external name. will be translated before showing
    -   **classname**: our class that extends VTTask
    -   **classpath**: the script on the file system that contains our
        new workflow
    -   **templatepath**: the Smarty template script on the file system
        that will show the configuration screen
    -   **modules**: a JSON array of module that the workflow is
        included and excluded from
    -   **sourcemodule**: the main module the workflow is related to, if
        this module is not installed/active the workflow will not be
        available. if left empty it will be available
    -   An example would be:
        -   "name"=&gt;"CBTagTask": internal reference name
        -   "label"=&gt;"CBTagTask": label to show on screen
        -   "classname"=&gt;"CBTagTask": name of the class to invoke to
            do the work
        -   "classpath"=&gt;"modules/com\_vtiger\_workflow/tasks/CBTagTask.inc":
            path to class that does the work
        -   "templatepath"=&gt;"com\_vtiger\_workflow/taskforms/CBTagTask.tpl":
            path to the smarty template
        -   "modules"=&gt;array('include' =&gt; array(),
            'exclude'=&gt;array()): available for all modules
        -   "sourcemodule"=&gt;'': not tied to any specific module
    -   you can [see more examples looking at the definitions of the preloaded workflow tasks](https://github.com/tsolucio/corebos/blob/master/build/changeSets/create_workflow_taskstype.php)

<!-- -->

-   Add new task file:
    *modules/com\_vtiger\_workflow/tasks/CBTagTask.inc*, which contains
    the class that will do the work. You can put the script anywhere you
    want in the application file system, but it has to be the same place
    indicated in the database record.

<!-- -->

-   The script *modules/com\_vtiger\_workflow/tasks/CBTagTask.inc*
    defines the base VTTask class extended for this case.
    -   The name of the class has to be the same we added in the
        database record in the first step
    -   Important is the *getFieldNames()* method where **simply adding
        a list of variables** they will get saved with no other work
        than to send them through REQUEST
    -   The *doTask()* method is where the action of the task has to be
        implemented

<!-- -->

-   Add translation strings for the new Task in
    *com\_vtiger\_workflow/language*
    ```
    'CBTagTask' => 'Add/Delete Tag',
    ```
<!-- -->

-   Add new task template file:
    *Smarty/templates/com\_vtiger\_workflow/taskforms/CBTagTask.tpl*
    -   This script must be inside the *Smarty/templates* directory and
        must be the same as the value we inserted in the database
    -   This template file can do any magic that is needed, usually
        using the module's base translation files for screen output.
        Special considerations are that we have available a *$task*
        object with the definitions of the task we are editing and this
        object has properties for each of the variables we defined in
        the *getFieldNames()* method.
    -   We simply have to create an HTML input or similar with the same
        name for it to be saved automatically

[You can see a full example of how we add a new workflow task to add and delete Tags](https://github.com/tsolucio/corebos/commit/ee0ef68abec95ffbd45dc382096cb7372645f0e2)
