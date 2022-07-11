---
Title: JMethods
---

##Replacing CompiledMethod with something better

Prioritaet: AST position paper. Deadline: 19.5

Dann: Plan Master

-  Zeitplan
-  Inhaltsplan
-  Besprechung mit Stef
Deadline: 1. Juni

Dann:

-  Implementierung \+ Experimente
-  Wenn moeglich, Paper.
-  TOC Master, sync with Stef
-  Dann ausarbeitung Master
-  Fertig.

###Zeitplan
```ende Juni: First draft of Table of Contents, besserer Name
ca. 15.9.06: Anfang schreiben Master
1.11.06 --> Abgabe.
Note kommt dann Anfang / Mitte Januar 
```


- [TOC](%base_url%/wiki/projects/archive/jmethods/toc)
- [Names](%base_url%/wiki/projects/archive/jmethods/names)
- [Talk Ideas](%base_url%/wiki/projects/archive/jmethods/talkideas)

###Ideen before/after Code für Methoden

-  &lt;before&gt;. &lt;code&gt; ensure: &lt;after&gt;
	-  einfach zu implementieren
	-  vergleichsweise kleiner overhead
	-  kein Zugriff auf Resultat, keine Manipulation von Argumenten

-  MethodWrapper mit alter Methode in Literal
	-  Zugriff auf Resultat, einfache Manipulation von Argumenten
	-  etwas grösserer Overhead (MethodContext statt BlockContext)
	-  funktioniert mit primites


###Todo shortterm

-  besserer Name für ByteNurse
-  search / rewrite rule
-  return value instrumentation for method
-  introduce temp at method level and use in instrumentations
-  choose compilation strategy based on instrumentations
-  self modifying code: self refactoring code (rename senders ...)
	-  api migration: html divNamed: do: -> html div id: ; with: 

-  move before/after method to MethodNode
-  #readsField: #wirtedField:
-  #replace: -> #instead:
-  [http://www.squeaksource.com/Gutenberg.html](http://www.squeaksource.com/Gutenberg.html)
-  annotations that don't appear in the sourcecode -> tests
-  version button shows original method too, do we want that?
-  estimate overhead better
-  when recompiling method, should properties stay?
-  improve and test ByteNurse
	-  result of message

-  implement #messages of JCompiledMethod with a visitor
-  annotated annotations?
-  ...
-  compiling really long methods with really many literals speed comparision
-  #removeUnusedTemp:
-  look at Monticello 2 Model
-  breakpoint
```test1
	self  assert: ( 1 &lt; 2).
```

-  work in ast interface, #dontInline, #evaluateAtCompiletime
-  before/after code for method, => method wrapper ?

###Todo longterm

-  Transactional memory
	-  for each message sent in a method make an atomic_ none
	-  change all sends to the atomic one
	-  before an assignment to an istance variable log old value and self
	-  maker when entered an exited, not for atomic_ ones

-  Lint
-  just pretty print
-  comments
-  title for project
-  make self in browser refer to method
-  bring world peace by increasing CompiledMethod codequality

###Done

-  <img src="http://img86.imageshack.us/img86/6605/colorer1we.png" alt="colorer"/>
-  &lt;asJavascript&gt;
-  interpreter
-  instrument for one object only
-  metasends
	-  tests
	-  instvars
	-  to objects (in literals)

-  evaluate at compiletime
-  why do tests take so long? -> #compileAll, fixed
-  do what ByteSurgeon does on the AST
-  block with pseudovariables as blockarguments for instrumentation #decompile #printString
-  rename JCompiledMethod to JMethod (and accessors too)
-  multivalued annotations
-  provide ByteSurgeon interface: #instrument:, #isSend, #isInstVarAccess, ....
-  annotate the AST with #before:, #after:, #instead:
-  make ASTTranslator that is aware of that
-  make RBFormatter that is aware of that
-  make sure JFormatter works with several annotations
-  instrumentation fucks up temp names
-  rename arguments and temps via manipulating AST (RenameTemporaryRefactoring>>#renameNode:)
-  annotate expression as assertion, don't compile it when in deployment mode (ASTTranstlator again)
-  annotate AST
	-  create new syntax: (primary) &lt;annotationKey: annotationValue&gt;
	-  no inline: (unknown ifTrue: [ ... ]) &lt;noInline&gt;
	-  introduce Unknown Boolean
	-  assertions: (aReceiver size &gt; 5)&lt;assertion&gt; , transfrom ast before translating it
	-  make RBProgramNodeVistor subclass that is avare of annotations and transforms ast
	-  make RBFormatter  subclass that is avare of annotations
	-  ByteNurse, like ByteSurgeon just simpler, (true := false)&lt;instead: (Transcript show: 'nono') &gt

-  look at [Java Annotations](%base_url%/wiki/projects/archive/jmethods/javaannotations)
-  make it work on 3.9
-  removed 5 unneeded classes
-  make project wiki
-  rename method via manipulating AST
	-  generated sourcecode with pretty prining
	-  generated bytecode via ASTTranslator -> IR
	-  stop VM from segfaulting
	-  wirte new code into changeset
	-  keep method category after changing AST
	-  make versions button work
	-  notify browser of method change

-  estimate overhead
-  properties for CompiledMethod and JCompiledMethod
	-  CompiledMethod knows JCompiledMethod via properties

-  only AST and CompiledMethod are stored in a JCompiledMethod
	-  AST is used for high-level stuff
	-  CompiledMethod is used for low level stuff

-  use new instead of old compiler
-  Compiler generates JCompiledMethod instead of CompiledMethod
-  shold #assertedNodes move to a ASTTranslator,
-  make Annotation object not association
-  move ast to goods, magma, omnibase, bad results for all
-  title for presentation

###Postponed

-  compress AST (externally), first results show olny 33% decrease in size
-  compile whole image, watch size increase

###Why and What

-  MOP: Gepetto
-  AOP
-  Tools (don't always parse), compiler aware of annotations (inlining, assertions, ...)
-  Typesystems (pluggable [notNull, escapedString])
-  Reflection (?Structure Model?)
-  VCS
-  Eiffel, pre/postcondition
-  refactorings

###What not

-  optimizing compiler (JIT)
-  slim binaries
-  code as xml

#Why Method \+ BR AST
More structure than just a list (Lisp). Closer to the mental model of the programmer

#Tools Ideas

-  pretty print
-  syntax highlight
-  compiler
-  breakpoint (release compile, strip source)
-  assertion
-  vcs (diff, merge, treematching, ...)
-  metainformation about method (author, timestamp, comment, links, documentation, estimated price, how often invoked ...)
	-  annotations

-  xml
-  lint
-  refactorings (browser)
-  interpreter

#Done, mini-Overview

-  &lt;evaluteAtCompiletime&gt;
-  &lt;noInline&gt;
-  &lt;assertion&gt;
-  instrumentation, aMethod #insturment/Messages/Assignments/Variables/Literals:, #insertAfter:/#insertBefore:/#replace:/#metasendTo:, blocks with pseudovariables as arguments
	-  metasend, to any object

``` 	method instrumentMessages: \[ :node |
		node isSelfSend ifFalse: \[
			node metasendTo: recorder ] ].
```

-  variables
```	method instrumentVariables: \[ :node |
		(node isInstance and: \[ node isRead ]) ifTrue: \[
			node replace: \[ :name | self perform: name ] ] ].
```

-  assignments
```	method instrumentAssignments: \[ :node |
		node insertAfter: \[ :variable | variable := variable + 30000 ] ].
```

-  messages
```	method instrumentMessages: \[ :node |
		node insertAfter: \[ receiver - argument ] ].
```

-  same only for one object without runtime check!
-  worked on db storage, failed (possibly recompile goods with gcc 2.95)
-  improved ast-api, MessageNode>>#isSelfSend, VariableNode>>#isRead/#isWrite/#isGlobal/#isInstance/#isTemp

#Future ideas

-  build something that is usable ;)
	-  tracer (for tests?)
	-  redirect self-sends (OmniBase, Lukas, Avi)
	-  fast block decompile (javascript, lukas)


#Problems

-  Tools
-  Debugger
-  incremental syntax highlight

#Todo outside of project

-  same thing for classes, annotations for classes and intance variables

##Links:
[Rethinking code documentation](http://www.cs.utexas.edu/%7Eakkartik/feed.cgi?codelog.html)
[RNA](http://www.merlintec.com:8080/hardware/19)
[http://dawis2.informatik.uni-essen.de/site/staff/shanenbe/projects/FreeAnnotations/](http://dawis2.informatik.uni-essen.de/site/staff/shanenbe/projects/FreeAnnotations/)
[http://www.iam.unibe.ch/~denker/temp/treevsbytes/](http://www.iam.unibe.ch/~denker/temp/treevsbytes/)
[http://kasoft.freeyellow.com/Central/Kasoft/Typeset/JavaTree/index.html](http://kasoft.freeyellow.com/Central/Kasoft/Typeset/JavaTree/index.html)
[http://intentsoft.com/](http://intentsoft.com/)
[http://www.edge.org/digerati/simonyi/simonyi_p2.html](http://www.edge.org/digerati/simonyi/simonyi_p2.html)
[http://martinfowler.com/articles/languageWorkbench.html](http://martinfowler.com/articles/languageWorkbench.html)