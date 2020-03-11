Python Tutorials, Jupyter Notebooks, and Self-Documenting Code: A Case Study1

### Zachary Bunch,  Phillip E. Pfeiffer, IV,  and Oluwafeyisayo Oyeniyi

### Department of Computing

### East Tennessee State University

### Johnson City, TN  37614-0711

{bunchz, phil, oyeniyi}@etsu.edu



**Abstract**

A Juypter-Notebook-based Python tutorial has been developed for students with a background in object-oriented (OO) compiled languages and minimal background in topics that include functional programming, floating point imprecision, and differences between designing for interpreted and compiled languages. This work included an effort to make the notebook&#39;s codes self-describing: an effort that was only succeed in part, due to Python&#39;s differences from mainstream compiled languages.

1. **1** Introduction

Digital texts have been an area of research since Suppes and Atkinson&#39;s &#39;60s-era experiments with interactive learning [CITATION InsND \l 1033]. In spite of concerns about their effectiveness (viz. [CITATION The13 \l 1033],[CITATION Wal17 \l 1033],[CITATION Fri18 \l 1033]), digital texts continue to attract attention because of their potential advantages over traditional texts: i.e., reduced footprint, better portability, environmental friendliness, customizability, improved engagement via multimedia, ease of upgrades, and reduced cost. For interactive texts, this also includes improved retention through contextual learning (viz. [CITATION Buc17 \l 1033], [CITATION Har18 \l 1033], [CITATION Bar19 \l 1033], [CITATION Wil19 \l 1033]).

This study was concerned with the development of an interactive, digital text for teaching Python to new programmers whose primary background is in OO languages. Python currently enjoys widespread use, as attested to by its ranking on sites like Tiobe, which as of March 2020 rated Python as the third most popular programming language, behind Java and C [CITATION Tio20 \l 1033]; its use in major corporations, like Amazon, Facebook, Google, Instagram, Spotify, and SurveyMonkey [CITATION Kup18 \l 1033],[CITATION QuiND \l 1033]; and the ready availability of Python courses from universities (e.g., [CITATION HarND \l 1033], [CITATION StaND \l 1033], [CITATION Mas12 \l 1033]) and vendors (e.g., [CITATION Cod20 \l 1033], [CITATION Dat20 \l 1033], [CITATION Uda20 \l 1033]) alike.

Contemporary Python courses regularly assume little or no background in programming and focus on rudimentary Python. This study sought to create an interactive Python tutorial for (e.g.) students in traditional computing programs that emphasize languages like Java, C++, and C to the virtual exclusion of mainstream scripting languages. In addition to Python&#39;s rudiments, the goal was to cover oft-neglected topics in basic OO curricula, including floating point imprecision, alternatives to if-statement-based run-time type inference, multiple inheritance, Python scoping directives, reduction, nested classes, and dynamic attribute interpretation via \_\_getattribute\_\_ and \_\_setattr\_\_.

Jupyter Notebooks was chosen for its popularity and capabilities. In [CITATION Per18 \l 1033], Perkel notes that GitHub supported 2.5 million Jupyter Notebooks as of September 2018. Perkel attributes Jupyter&#39;s popularity to its replaceable kernel, which has allowed users to customize it for different programming languages, environments, and application domains. Additionally, Moore [CITATION Mic09 \l 1033]observes that Jupyter supports interactive learning by allowing developers to combine code with a narrative, engaging students whenever they execute a notebook&#39;s cell.



1. **2** Related Work
  1. **2.1** Self-documenting code

According to Knuth [CITATION knu84 \l 1033], the idea of self-documenting code is at least as old as Hoare&#39;s keynote address to the 1973 ACM Symposium on Programming Languages. Knuth&#39;s contribution to self-documenting code was Literate Programming: a view of programming as a process that develops &quot;works of literature&quot; that explain a developer&#39;s intentions to others. Other early attempts to promote self-documenting code include Bentley&#39;s recurring column in the Communications of the ACM (viz. [CITATION Ben86 \l 1033], [CITATION Ben861 \l 1033]) and Frakes et al.&#39;s retrospective on UNIX/C development at AT&amp;T [CITATION Fra91 \l 1033]. On the whole, since Knuth, the focus has shifted from the use of macro preprocessors to translate key phrases to formal codes to the writing of clear code proper and the development of very high level domain-specific languages, like RSpec [CITATION Beh20 \l 1033] and its descendants.

While code clarity is a standard best practice, practitioners differ with regard to the degree to which programs can be self-describing. One school of thought holds that a program should be completely understandable from its code and its unit tests: i.e., &quot;the only non-code definition should be for users.&quot; [CITATION Cun14 \l 1033]. Others note the inability of &quot;pure&quot; code to document why a program was written or why one approach was favored over another (e.g., [CITATION Ras05 \l 1033], [CITATION Atw06 \l 1033]); to make a language&#39;s idioms self-describing; or to address its libraries&#39; deficiencies in naming its methods (e.g., [CITATION Lai19 \l 1033]).

1.
  1. **2.2** Interactive Python textbooks

Examples of interactive courses on Python include da Fonseca and Race&#39;s notebooks for first-year undergraduate students [CITATION Adm16 \l 1033]; Pussinen&#39;s beginner notebooks [CITATION Pus18 \l 1033]; and a myriad of commercial &quot;Python for beginners&quot; courses, like Udemy&#39;s &quot;Complete Python Bootcamp&quot; [CITATION Ude20 \l 1033]. Notebooks for individuals with some background in programming have proven more difficult to identify. VanderPlas [CITATION Van16 \l 1033] focuses entirely on the procedural and functional elements of Python, bypassing classes and considerations related to OO programming. Prabhu [CITATION Pra20 \l 1033] focuses on Python for data science, omitting (e.g.) material on class definition. Pussinen&#39;s intermediate notebooks (op. cit.) cover additonal constructs, library functions, selected best practices, and pytest. Beaumont [CITATION Bea20 \l 1033] covers descriptors: classes that preprocess and/or postprocess values, by (e.g.) range-checking them or logging their uses.



1. **3** Goals

The original Tour of Python was developed by the paper&#39;s second author over roughly 15 years of teaching Python in a variety of upper-division and graduate courses. In its final form, it was an 8,000-line text file that offered an in-depth, hands-on approach to learning Python 3.7. Its eight sections covered installing and running Python; Python values; control structures, and functions; functional language features; classes; object oriented programming techniques; and modules. An appendix presented sample Python programs, including seven increasingly concise versions of a prime-number-computing program and a nine-line version of Conway&#39;s Game of Life.

Work focused on four goals: converting this tutorial to a Juypter-Notebook format; rearchitecting it as a series of small, self-contained examples; extending its content to address gaps in the original; and revising its codes to make them readable by programmers who are new to Python, without comments.



1. **4** Methodology

The conversion from text file to notebook form proceeded in three phases. During the first phase of work, the original text file was converted to markdown en bloc. This process included some modest upgrades to the original tour, largely inspired by the first author&#39;s initial lack of familiarity with interpreted languages and a review of Udemy&#39;s course materials, Areas of particular concern included lambda expressions, scoping directives, rules Boolean coercions, and Python&#39;s four formalisms for string formatting.

In the second phase, the initial Tour&#39;s large blocks of examples were broken into multiple, smaller examples, each of which focused on one language feature or design practice. This effort exposed needs for further examples and sample problems and for rearranging material in the original, including new sections on identifiers and internal mechanisms for documentation.

In the third phase, McConnell&#39;s guidelines for programming style  [CITATION McC04 \l 1033]were used to review and rework the Tour&#39;s examples. Additionally, appendices were added on installing and using Python outside of Jupyter.



1. **5** Discussion
  1. **5.1** Impressions of Jupyter Notebooks

Jupyter&#39;s Python 3 kernel poses a variety of previously noted obstacles for authoring notebooks (viz. [CITATION Ken17 \l 1033], [CITATION Mue18 \l 1033]). Issues with this model that complicated work on the Tour are discussed below.

**Configuration issues.** Prior to version 3.8, Python&#39;s run-time engine for Windows used a reactor-pattern-based strategy to service event loops. In 3.8, this changed to a proactor-based mechanism, which rendered Python incompatible with one of Jupyter&#39;s core components. This issue can be corrected by adding code to a module that resets the component&#39;s event-loop handler [CITATION var20 \l 1033]—a change that casual users should not be required to make.

**Order of execution issues.** Jupyter allows users to execute a notebook&#39;s cells in any order. Since Jupyter&#39;s codes all share a common environment, the out-of-order execution of a notebook&#39;s cells may yield unexpected outcomes. Consider, for example, an exercise involving four consecutive cells with the following four codes:

1. 1)f = lambda x: x+3
2. 2)f = lambda x: x+2
3. 3)y = f(2)
4. 4)assert y == 4, &#39;this should not fail&#39;

Executing 2, 1, then 3 will cause 4 to fail, as will executing 1, then 3 [CITATION Gru20 \l 1033].

Zielnicki [CITATION Zie17 \l 1033]addresses this issue with a plugin that uses dependency analysis to identify the predecessor cells upon which a given cell&#39;s computation presumably depends, then updates that cell&#39;s values automatically when one of those upstream variables changes. The Tour avoids this problem by framing each example as a self-contained code.

**Asynchronous execution**. Jupyter supports concurrent cell execution: i.e., a user who executes the contents of a long-running cell can execute other cells while the first is running. Jupyter indicates that a cell has not yet completed by showing [\*] next to the cell: a convention that may not be obvious inexperienced users. A more visually compelling &quot;execution in progress&quot; indicator would allow authors to avoid adding such indicators to their codes.

**Lack of versioning**. Jupyter fails to provide a built-in mechanism for versioning notebooks, an oft-voiced concern (viz. [CITATION Sch19 \l 1033]). This lack of source control also complicates efforts at collaboration.

**Autosaving**. By default, Jupyter&#39;s Python 3 kernel saves an open notebook&#39;s state to its backing file every 120 seconds. This default behavior complicates notebook creation by interfering with the creation of &quot;virgin&quot; notebooks. Autosaving updates the contents of a file&#39;s initially empty &quot;Out&quot; cells, which capture the executions of their corresponding &quot;In&quot; cells. More insidiously, it updates text cells that were &quot;executed&quot; by (e.g.) a naive author who &quot;shift-enters&quot; his or her way through a notebook. Executing a text cell updates the cell&#39;s markdown, obliterating any non-essential line-breaks that were inserted into the markdown text for readability.

Autosaving can be disabled by updating Jupyter&#39;s configuration file [CITATION Spa17 \l 1033] or executing%autosave 0 in a notebook cell. Novice users, however, would be better served by a menu option that includes a control for modifying Jupyter&#39;s autosave interval.

**Low performance for large notebooks**. Table 1 shows the time that Firefox, Opera, and Chrome browsers to load a single-file version of the Tour, relative to three host platforms. This Tour was a considerably shorter version of the current Tour that omitted the appendices and other newer material. Tests was conducted by clearing a browser&#39;s cache, then executing jupyter notebook &quot;Tour of Python.ipynb&quot; from a Windows command prompt. In each case, the Jupyter framework proper loaded quickly, taking roughly 4 seconds on Chrome, 5 on Firefox, and 5-6 on Opera. These tests suggested a need to &quot;burst&quot; the tour into separate notebooks for usability.

Table 2 shows the time that the three browsers needed to load the largest file in a second, multi-file version of Tour (5. Built-in data structures.ipynb). These shorter load times were deemed acceptable for the updated Tour.

1.
  1. **5.2** Constructing self-documenting code

Efforts to craft self-documenting code met with varying degrees of success. In all cases where Python&#39;s idioms were deemed too foreign for the Tour&#39;s audience to be self-explanatory, introductory texts and in-code comments were used to supplement the examples.

**Classes**. As a rule, simple classes with straightforward names like CardDeck and Suit were used to illustrate Python&#39;s support for OO. Elements of Python that were deemed to warrant comments included staticmethods and classmethods; nested classes; special identifiers, like \_\_init\_\_, \_\_eq\_\_, and \_\_ne\_\_; multiple inheritance and \_\_mro\_\_; the intended uses of \_\_str\_\_and \_\_repr\_\_; \_\_getattribute\_\_, \_\_setattr\_\_, and dynamic attribute interpretation; name mangling; and Python&#39;s lack of support for overloading.

**Naming**. As a rule, identifier names were chosen that reflected their intent. Exceptions were made for very short functions, like one that deletes itself after it runs once. Aspects of Python&#39;s functions that were deemed to warrant additional explanation included functions as objects with properties and lifetimes, nested and variadic functions, generators; and lambda expressions.Aspects of Python&#39;s data structures that were deemed to warrant additional explanation included the distinction between mutable and immutable data types and its rationale, and a rationale for the confusing array of string formatting mechanisms that Python now supports.

**Control**. While basic control structures like if, while, and try/except have direct analogues in mainstream compiled languages, Python is fraught with idioms that are particular to Python and/or functional languages. These include sequence-based for loops; comprehensions; the reduce functional; and Python&#39;s global and nonlocal scope-control declarations.

**Design**. Differences between elements of compiled and interpreted languages favor different approaches to mid- and low-level design. Aspects of Python-centric approaches to design that were deemed to warrant additional explanation included latent (a.k.a. &quot;duck&quot;) typing; abstract base classes as a convention; data hiding as a convention; heterogeneous data structures; the use of variadic parameter lists and keyword arguments as an alternative to overloading.; and the need to exercise infrequently traversed paths through routine during testing, as a way of avoiding (e.g.) &quot;copy-paste-and-change-somewhat&quot; errors in error-handling logic.

**Other**. Apart from Python&#39;s idioms, the single biggest impediment to crafting self-describing code was Python&#39;s standard library. The purpose of objects with names like importlib.invalidate\_caches, time.strftime, sys.path,os.walk, and filestat.st\_ctime, while useful for writing concise codes, is not immediately obvious from their names.

1.
  1. **5.3** Student feedback

Pending.

| **Platform** | _MS Windows 7 Ultimate SP 1 __v.6.1 build 7601__ Dell 4600, 16 GB Ram_ | _MS Windows 10 __v.1909 build 18363.592__ Dell Precision 7510, 32 GB Ram_ | _MS windows 10 education __v.1809 build 17763.963__ Dell 2-in-1, 16 GB Ram_ |
| --- | --- | --- | --- |
| **Browser** |
| _Firefox 72.0.2_ | 19-21 seconds | 19-21 seconds | 15 seconds |
| _Opera  66.0.3515.72_ | 28 seconds | 24-25 seconds | 33-35 seconds |
| _Chrome  80.0.3987.87_ | 30-32 seconds | 29-30 seconds | 30-32 seconds |

Table 1.  Load times for single-notebook Tour.  Notebook size: 8,077 lines, 309 KB.  All platforms are 64-bit.

| **Platform** | _MS windows 7 Ultimate SP 1 __v.6.1 build 7601__ Dell 4600, 16 GB Ram_ | _MS Windows 10 __v.1909 build 18363.592__ Dell Precision 7510, 32 GB Ram_ | _MS windows 10 education __v.1809 build 17763.963__ Dell 2-in-1, 16 GB Ram_ |
| --- | --- | --- | --- |
| **Browser** |
| _Firefox 72.0.2_ | 10-11 seconds | 8-9 seconds | 8-9 seconds |
| _Opera  66.0.3515.72_ | 11-12 seconds | 8-9 seconds | 10-11 seconds |
| _Chrome  80.0.3987.87_ | 8 seconds | 8 seconds | 8 seconds |

Table 2. Load times for largest section of multi-section Tour.  Size: 1,900 lines, 69 KB.  All platforms are 64-bit.



#

References


References

| [1] | Institute of Progressive Education and Learning, &quot;History of eLearning &amp; Interactive Books,&quot; N.D.. [Online]. Available: http://institute-of-progressive-education-and-learning.org/elearning-i/history-of-elearning/. [Accessed 24 01 2020]. |
| --- | --- |
| [2] | The Hechinger Report, &quot;Next to the book, nothing will change education more than digital learning,&quot; 31 10 2013. [Online]. Available: https://hechingerreport.org/next-to-the-book-nothing-will-change-education-more-than-digital-learning/. [Accessed 24 01 2020]. |
| [3] | C. Wallis, &quot;A textbook dilemma: Digital or paper?,&quot; 23 08 2017. [Online]. Available: https://hechingerreport.org/textbook-dilemma-digital-paper/. [Accessed 24 01 2020]. |
| [4] | N. Friesen, &quot;Despite predictions of their demise, college textbooks aren&#39;t going away,&quot; 23 08 2018. [Online]. Available: https://theconversation.com/despite-predictions-of-their-demise-college-textbooks-arent-going-away-99931. [Accessed 24 01 2020]. |
| [5] | S. Buckles, &quot;Students Are Learning Differently. Interactive Textbooks Can Help,&quot; 14 06 2017. [Online]. Available: https://tophat.com/blog/students-interactive-textbooks/. [Accessed 02 02 2020]. |
| [6] | M. Harman, &quot;9 Benefits of Interactive eBooks,&quot; 10 07 2018. [Online]. Available: https://kitaboo.com/9-benefits-of-interactive-ebook/. [Accessed 24 01 2020]. |
| [7] | L. A. Barba and L. J. Barker, &quot;Teaching and Learning with Jupyter,&quot; 06 12 2019. [Online]. Available: https://jupyter4edu.github.io/jupyter-edu-book/index.html. [Accessed 17 12 2020]. |
| [8] | J. Wilber, &quot;10 Reasons Why eBooks Are Better Than Print,&quot; 12 06 2019. [Online]. Available: https://owlcation.com/humanities/10-Reasons-Why-eBooks-are-Better-than-Print-Books. [Accessed 24 01 2020]. |
| [9] | Tiobe, &quot;Tiobe Index for March 2020,&quot; 03 2020. [Online]. Available: https://www.tiobe.com/tiobe-index/. [Accessed 06 03 2020]. |
| [10] | V. Kuprenko, &quot;5 Huge Tech Companies That Use Python: Does It Fit Your Project?,&quot; 26 01 2018. [Online]. Available: https://www.cleveroad.com/blog/discover-5-leading-companies-that-use-python-and-learn-does-it-fit-your-project. [Accessed 24 01 2020]. |
| [11] | Quintagroup, &quot;Python at Google,&quot; N.D.. [Online]. Available: https://quintagroup.com/cms/python/google. [Accessed 24 01 2020]. |
| [12] | Harvard University, &quot;Online Python Courses,&quot; N.D.. [Online]. Available: https://online-learning.harvard.edu/subject/python. [Accessed 24 01 2020]. |
| [13] | Stanford School of Engineering, &quot;Introduction to Python,&quot; N.D.. [Online]. Available: https://online.stanford.edu/courses/xfds113-introduction-python. [Accessed 24 01 2020]. |
| [14] | Massachusetts Institute of Technology, &quot;MIT OpenCourseWare Publishes Unique Introductory Python Programming Independent Study Course,&quot; 02 03 2012. [Online]. Available: https://ocw.mit.edu/about/press-releases/introduction-to-computer-science-and-programming-scholar/. [Accessed 24 01 2020]. |
| [15] | CodeCadamy, &quot;Python,&quot; 2020. [Online]. Available: https://www.codecademy.com/catalog/language/python. [Accessed 24 01 2020]. |
| [16] | DataCamp, &quot;Data Science Courses R &amp; Python,&quot; 2020. [Online]. Available: https://www.datacamp.com/courses/tech:python?utm\_source=adwords\_ppc&amp;utm\_campaignid=1565610360&amp;utm\_adgroupid=63334254150&amp;utm\_device=c&amp;utm\_keyword=%2Bpython%20%2Bcourse&amp;utm\_matchtype=b&amp;utm\_network=g&amp;utm\_adpostion=3o3&amp;utm\_creative=295213502780&amp;utm\_targetid=k. [Accessed 24 01 2020]. |
| [17] | Udacity, &quot;Introduction to Python Programming,&quot; 2020. [Online]. Available: https://www.udacity.com/course/introduction-to-python--ud1110. [Accessed 24 01 2020]. |
| [18] | J. M. Perkel, &quot;Why Jupyter is data scientists&#39; computational notebook of choice,&quot; 30 10 2018. [Online]. Available: https://www.nature.com/articles/d41586-018-07196-1. [Accessed 02 02 2020]. |
| [19] | M. Moore, &quot;Three types of interaction,&quot; _American Journal of Distance Education,_ vol. 3, no. 2, pp. 1-7, 2009. |
| [20] | D. Knuth, &quot;Literate Programming,&quot; _The Computer Journal,_ vol. 27, no. 2, pp. 97-111, 1984. |
| [21] | J. Bentley and D. Knuth, &quot;Programming Pearls: Literate Programming,&quot; _Communications of the ACM,_ vol. 29, no. 5, pp. 369-384, 05 1986. |
| [22] | J. Bentley, D. Knuth and D. McIlroy, &quot;Programming Pearls: A Literate Program,&quot; _Communications of the ACM,_ vol. 29, no. 6, pp. 471-483, 05 1986. |
| [23] | W. B. Frakes, C. J. Fox and B. A. Nemjeh, Software Engineering in the UNIX/C Environment, Prentice Hall, Inc., 1991. |
| [24] | &quot;Behaviour Driven Development for Ruby. Making TDD Productive and Fun,&quot; [Online]. Available: https://rspec.info/. [Accessed 21 02 2020]. |
| [25] | Cunningham and Cunningham, &quot;&quot;self-documenting software&quot;,&quot; 03 12 2014. [Online]. Available: https://wiki.c2.com/?SelfDocumentingCode. [Accessed 01 02 2020]. |
| [26] | J. Raskin, &quot;Comments Are More Important Than Code,&quot; _ACM Queue,_ vol. 3, no. 2, March 2005. |
| [27] | J. Atwood, &quot;Code Tells You How, Comments Tell You Why,&quot; 18 12 2006. [Online]. Available: https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/. [Accessed 01 02 2020]. |
| [28] | C. Laine, &quot;Self-documenting code is (mostly) nonsense,&quot; 16 06 2019. [Online]. Available: https://medium.com/it-dead-inside/self-documenting-code-is-mostly-nonsense-1de5f593810f. [Accessed 01 02 2020]. |
| [29] | J. Q. da Fonseca and C. Race, &quot;Using Jupyter Notebooks to teach computational literacy,&quot; 16 May 2016. [Online]. Available: http://www.elearning.fse.manchester.ac.uk/blog/2016/05/16/using-jupyter-notebooks-to-teach-computational-literacy/. |
| [30] | J. Pussinen, &quot;Learn Python 3,&quot; 27 10 2018. [Online]. Available: https://github.com/jerry-git/learn-python3. [Accessed 22 02 2020]. |
| [31] | Udemy, Inc,, &quot;Python Bootcamp,&quot; 2020. [Online]. Available: https://www.udemy.com/course/complete-python-bootcamp/. [Accessed 22 02 2020]. |
| [32] | J. VanderPlas, A Whirlwind Tour of Python, K. Brown and J. Kwityn, Eds., Sevastapol, CA: O&#39;Reilly Media, Inc, 2016. |
| [33] | T. N. Prabhu, &quot;Python,&quot; 20 02 2020. [Online]. Available: https://nbviewer.jupyter.org/github/Tanu-N-Prabhu/Python/tree/master/. [Accessed 21 02 2020]. |
| [34] | C. Beaumont, &quot;Python Descriptors Demystified,&quot; [Online]. Available: https://nbviewer.jupyter.org/gist/ChrisBeaumont/5758381/descriptor\_writeup.ipynb. [Accessed 22 02 2020]. |
| [35] | S. McConnell, Code Complete, Safari, 2004, p. Chapter 32. |
| [36] | O. Kenway, &quot;Why I don&#39;t like Jupyter Notebooks,&quot; 03 10 2017. [Online]. Available: https://owainkenwayucl.github.io/2017/10/03/WhyIDontLikeNotebooks.html. [Accessed 07 02 2020]. |
| [37] | A. Mueller, &quot;5 reasons why jupyter notebooks suck,&quot; 24 03 2018. [Online]. Available: https://towardsdatascience.com/5-reasons-why-jupyter-notebooks-suck-4dc201e27086. [Accessed 07 02 2020]. |
| [38] | various, &quot;Jupyter Notebook with Python 3.8 - NotImplementedError,&quot; 02 02 2020. [Online]. Available: https://stackoverflow.com/questions/58422817/jupyter-notebook-with-python-3-8-notimplementederror. [Accessed 07 02 2020]. |
| [39] | J. Grus, _private communication,_ 2020. |
| [40] | K. Zielnicki, &quot;Nodebook: Stitch Fix Technology,&quot; 26 07 2017. [Online]. Available: https://multithreaded.stitchfix.com/blog/2017/07/26/nodebook/. [Accessed 23 02 2020]. |
| [41] | D. Schmudde, &quot;How to Version Control Jupyter Notebooks,&quot; 08 11 2019. [Online]. Available: https://nextjournal.com/schmudde/how-to-version-control-jupyter. [Accessed 07 02 2020]. |
| [42] | M. Spacek, &quot;Turn Off Autosave in IPython Notebook,&quot; 31 08 2017. [Online]. Available: https://stackoverflow.com/questions/25631344/turn-off-autosave-in-ipython-notebook. [Accessed 07 02 2020]. |



1\*Copyright ©2020 by the Consortium for Computing Sciences in Colleges.  Permission to copy without fee all or part of this material is granted provided that the copies are not made or distributed for direct commercial advantage, the CCSC copyright notice and the title of the publication and its date appear, and notice is given that copying is by permission of the Consortium for Computing Sciences in Colleges. To copy otherwise, or to republish, requires a fee and/or specific permission.
