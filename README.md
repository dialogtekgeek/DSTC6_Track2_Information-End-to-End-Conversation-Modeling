# DSTC6_Information-End-to-End-Conversation-Modeling
Please go to the following link:
https://github.com/dialogtekgeek/DSTC6-End-to-End-Conversation-Modeling

1. Main task (mandatory): Customer service dialog using Twitter

    (*) The tools to download twitter data and extract the dialog text are provided to all attendees at DSTC6 Track #2. 
      The attendees need to collect the data by themselves. The data collected before Aug. 1st are available as trial data, 
      and the official training/development data will be collected from Aug. 1st to 31st .

    Task A: Full or part of the training data will be used to train conversation models.

    Task B: Any open data, e.g. from web, are available as external knowledge to generate informative sentences. But they should not overlap
with the training, validation and test data provided by organizers.

2. Pilot task: Movie script dialog using OpenSubtitles

# Necessary steps

The tools and data sets are available for the DSTC6 attendees. 
Please visit the following page to make your registration.

    http://workshop.colips.org/dstc6/index.html

We will provide the access token to download the data collection tools and the baseline system.

## Preparation
Most tools are written in python, which were tested on python2.7.6+ and python3.4.1+,
and some bash scripts are also used to execute those tools.

For data preparation, you will need additional python modules as follows:

* six
* tqdm
* nltk

which can be installed by
```
pip install <module-name>
```
or
```
pip install <module-name> -t <some-directory>
```
where `<some-directory>` is a directory storing python modules and needs to be accessible from python,
e.g. by including it in PYTHONPATH environment variable.

If you try the baseline system, you will need Chainer <http://chainer.org> ,a deep learning toolkit, 
to perform training and evaluation of neural conversation models.
Please follow the instruction in `ChatbotBaseline/README.md`.

## Twitter task

1. prepare data set using `collect_twitter_dialogs` scripts.

    ```
    $ cd collect_twitter_dialogs
    $ collect.sh
    ```
    (a twitter account and access keys are necessary to run the script. follow the instruction in `collect_twitter_dialogs/README.md`)
   
2. extract training, development and test sets from the stored twitter dialog data
    
    ```
    $ cd ../tasks/twitter
    $ make_trial_data.sh
    ```
    
    Note: the extracted data are trial data at this moment.

3. run baseline system (optional)

    ```
    $ cd ../../ChatbotBaseline/egs/twitter
    $ run.sh
    ```
    
    (see `ChatbotBaseline/README.md`)

## OpenSubtitles task

1. download OpenSubtitles2016 data

    ```
    $ cd tasks/opensubs
    $ wget http://opus.lingfil.uu.se/download.php?f=OpenSubtitles2016/en.tar.gz
    $ tar zxvf en.tar.gz
    ```

2. extract training, development and test sets from the stored subtitle data 

    ```
    $ make_trial_data.sh
    ```
    Note: the extracted data are trial data at this moment.

3. run baseline system (optional)

    ```
    $ cd ../../ChatbotBaseline/egs/opensubs
    $ run.sh
    ```
    
    (see `ChatbotBaseline/README.md`)
    
## Directories and files
* README.md : this file
* tasks : data preparation for each subtask
* collect_twitter_dialogs : scripts to collect twitter data
* ChatbotBaseline : a neural conversation model baseline system

## Contact Information 
You can get the latest updates and participate in discussions on DSTC mailing list

To join the mailing list, send an email to: (listserv@lists.research.microsoft.com) putting "subscribe DSTC" in the body of the message (without the quotes). To post a message, send your message to: (dstc@lists.research.microsoft.com).
