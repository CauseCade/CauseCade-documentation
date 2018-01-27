#### Structure

We have the following types of teaching material in causecade:
1. courses
2. lessons
3. example networks


Courses contain lessons, and contain *references* to example networks. Lesson text and network contents are stored in markdown
and JSON files respectively. These are stored in the causecade-lessons and causecade-networks repositories on GitHub. 


In order to allow for on the fly ajustment of teaching material of CauseCade without having to compile the whole application each time, 
the whole course structure is specified elsewhere. The teaching material structure is specified in the meta.json file in the 
causecade-lessons repository. 

#### Creating new Courses

Courses are the higest level of teaching material in causecase. They have the following properties, specified in meta.json:
1. name
2. date of creation *[currently unused property]*
3. a list of all the lessons
4. network URL list (contains the URLs of the networks that are relevant for the lessons in this course)
5. network name list (names for the networks specified in the URLs, in order of the above URLs)
6. description *[currently unused property]*
7. category *[currently unused property]*

#### Creating new lessons

Lessons must be specified in the meta.json file, inside the lessonlist section. They have the following properties:
1. name
2. date of creation *[currently unused property]*
3. date of last update *[currently unused property]*
4. brief description (one or two sentences)
5. lesson URL (where the .md file can be fetched from)
6. lesson index (specifies which network from the network URL list in the course belongs to this lesson. Starts at 1, not 0)

#### Creating new (example) networks

Networks are fully specified in their own JSON file. If a network is to be tied to a specific lesson,
it's URL and a display name should be added to meta.json in the right course. Additionally, in meta.json,
one should specify the right index for the lesson that this networks belongs to. (see above and meta.json)


Networks have the following properties:
1. name
2. nodelist (containing all the nodes of the network)  
3. linklist (containing all the links)


Where nodes have the following properties:
1. name
2. statecount (how many states each node/random variable has)
3. the labels for each state (e.g 'true','false')
4. ~~isInstantiated (whether this node has been observed/measured)~~ (deprecated 27-01-18)
5. ConditionalProbabilityTable(CPT) (Matrix containing the conditional probability distribution)
6. Posterior (probability of this node)
7. Lambda Evidence (evidence this node has gotten from it's descendants) (amount of entries should match statecount)
8. Pi Evidence (evidence this node has gotten from it's ancestors) (amount of entries should match statecount)


Where links have the following properties:
1. origin (startpoint of directed link) (name of node)
2. target (endpoint of directed link) (name of node)

