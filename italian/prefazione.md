## Prefazione

> Unix non è tanto un sistema operativo quanto una storia orale.

\~ Neal Stephenson

C’è una gran differenza fra conoscenza ed esperienza. La conoscenza ti
permette di dedurre la cosa giusta da fare; l’esperienza rende la cosa
giusta un riflesso, che difficilmente richiede un pensiero del tutto
cosciente.

Questo libro ha un sacco di conoscenza in se, ma è soprattutto a
proposito dell’esperienza. L’intenzione è provare ad insegnare le cose a
proposito dello sviluppo Unix che gli esperti conoscono, ma che non
sanno di conoscere. È quindi meno sui dettagli tecnici e più sulla
cultura condivisa, rispetto alla maggior parte dei libri su Unix:
cultura sia esplicita che implicita, tradizioni sia consapevoli che
inconsapevoli. Non è un libro su “come-fare”, ma sul “perché-fare”. Il
perché-fare ha molta più importanza pratica, perché troppo software è
stato mal progettato. Molti di questi soffrono di pesantezza, sono
eccessivamente difficili da mantenere, e troppo difficili da convertire
per nuove piattaforme o estendere in modi che il programmatore originale
non aveva previsto. Questi problemi sono sintomo di una cattivo design.
Speriamo che i lettori potranno imparare qualcosa su ciò che Unix ha da
insegnare loro a proposito di un buon design.

Questo libro è divisio in quattro parti: Contesto, Design, Tools e
Comunità.

La prima parte (Contesto) è filosofia e storia, per fornire le basi e le
motivazioni a ciò che segue.  
La seconda parte (Design) dispiega i principi della filosofia Unix in
consigli più specifici sul design e l’implementazione.  
La terza parte (Tools) si concentra sul software che Unix fornisce per
aiutarti a risolvere i problemi.  
La quarta parte (Comunità) è sulle transazioni fra umani e sugli accordi
che rendono la cultura Unix così efficace in quello che fa.

Poiché questo libro è a proposito della cultura condivisa, non ho mai
pensato di scriverlo da solo. Noterai che il testo include apparizioni
di sviluppatori Unix di primo piano, coloro che hanno plasmato la
tradizione Unix.

Il libro ha attraversato un prolungato processo di revisione pubblica,
durante il quale ho invitato questi luminari a commentare e discutere
sul testo. Piuttosto che sommergere i risultati di tale processo nella
versione finale, questi ospiti sono stati incoraggiati a parlare con le
proprie voci, amplificando, sviluppando e anche mostrandosi in
disaccordo con la linea principale del testo.

In questo libro, quando uso l’editoriale “noi” non è per fingere
l’onniscienza, ma per riflettere il fatto che si tenta di articolare
l’esperienza di un’intera comunità. Poiché qesto libro è incentrato sul
trasmettere la cultura, include molto di più in termini di storia,
folklore e disgressioni di quanto sia normale per un libro tecnico.
Divertiti; anche queste cose fanno parte della tua educazione come
programmatore Unix. Nessuno dei singoli dettagli storici è vitale, ma la
somma di tutti questi è importante. Pensiamo che questo renda la storia
un po’ più interessante. Ma ancora più importante, capire da dove Unix è
venuto e come è diventato quello che è vi aiuterà a sviluppare un senso
intuitivo per lo stile Unix. Per la stessa ragione, ci rifiutiamo di
scrivere come se la storia fosse finita. Troverete un numero
inusualmente elevato di riferimenti al momento della stesura di questo
libro. Non vogliamo far finta che la prassi attuale rifletta una qualche
sorta di risultato senza tempo perfettamente logico preordinato dal
destino. I riferimenti al tempo della scrittura sono da intendersi come
un avvertimento per il lettore tra due, tre o cinque anni che le
dichiarazioni o i fatti potrebbero essere diventati datati e dovrebbero
essere ricontrollati.

Fra le altre cose questo libro non è ne una guida al C, ne una guida ai
comandi e alle API Unix. Non è una guida di riferimento per _sed_,
_yacc_, Perl o Python. Non è un testo elementare di programmazione di
rete, ne un esaustiva guida ai misteri di X. Non è neanche un tour degli
interni e dell’architettura di Unix. Altri libri coprono queste meglio
questi casi specifici, e questo libro ti rimanda ad essi quando
necessario. Al di là di tutte queste specifiche tecniche, la
cultura Unix ha una tradizione ingegneristica non scritta che ha
sviluppato letteralmente oltre milioni di anno-uomo di sforzi da parte
di esperti. Questo libro è scritto nella convinzione che la
comprensione di questa tradizione, e l’aggiunta dei suoi
modelli di design al vostro toolkit, vi aiuterà a diventare
programmatori e designer migliori. Le culture sono costituite da
persone, e il modo tradizionale di imparare la cultura Unix è dalle
altre persone e attraverso il folklore, per osmosi. Questo libro
non è un sostituto per l’acculturazione fra persone, ma può
contribuire ad accelerare il processo permettendo di toccare
l’esperienza degli altri.


## Who Should Read This Book

You should read this book if you are an experienced Unix programmer who
is often in the position

of either educating novice programmers or debating partisans of other
operating systems, and you

find it hard to articulate the benefits of the Unix approach.

You should read this book if you are a C, C++, or Java programmer with
experience on other

operating systems and you are about to start a Unix-based project.

1 The three and a half decades between 1969 and 2003 is a long time.
Going by the historical trend curve in number of Unix

sites during that period, probably somewhere upwards of fifty million
man-years have been plowed into Unix development

worldwide.

xvii

Preface

You should read this book if you are a Unix user with novice-level up to
middle-level skills in

the operating system, but little development experience, and want to
learn how to design software

effectively under Unix.

You should read this book if you are a non-Unix programmer who has
figured out that the Unix

tradition might have something to teach you. We believe you’re right,
and that the Unix philosophy

can be exported to other operating systems. So we will pay more
attention to non-Unix environments

(especially Microsoft operating systems) than is usual in a Unix book;
and when tools and case

studies are portable, we say so.

You should read this book if you are an application architect
considering platforms or implemen-

tation strategies for a major general-market or vertical application.

It will help you understand

the strengths of Unix as a development platform, and of the Unix
tradition of open source as a

development method.

You should *not * read this book if what you are looking for is the
details of C coding or how to use

the Unix kernel API. There are many good books on these topics;
*Advanced Programming in the*

*Unix Environment *[*\[Stevens92\] *](#536)is classic among explorations
of the Unix API, and *The Practice of*

*Programming *[*\[Kernighan-Pike99\] *](#532)is recommended reading for
all C programmers (indeed for all

programmers in any language).

How to Use This Book

This book is both practical and philosophical. Some parts are aphoristic
and general, others will

examine specific case studies in Unix development. We will precede or
follow general principles

and aphorisms with examples that illustrate them: examples drawn not
from toy demonstration

programs but rather from real working code that is in use every day.

We have deliberately avoided filling the book with lots of code or
specification-file examples, even

though in many places this might have made it easier to write (and in
some places perhaps easier

to read!). Most books about programming give too many low-level details
and examples, but fail at

giving the reader a high-level feel for what is really going on. In this
book, we prefer to err in the

opposite direction.

Therefore, while you will often be invited to read code and
specification files, relatively few are

actually included in the book. Instead, we point you at examples on the
Web.

xviii

Preface

Absorbing these examples will help solidify the principles you learn
into semi-instinctive working

knowledge. Ideally, you should read this book near the console of a
running Unix system, with a Web

browser handy. Any Unix will do, but the software case studies are more
likely to be preinstalled

and immediately available for inspection on a Linux system. The pointers
in the book are invitations

to browse and experiment. Introduction of these pointers is paced so
that wandering off to explore

for a while won’t break up exposition that has to be continuous.

Note: While we have made every effort to cite URLs that should remain
stable and usable, there is

no way we can guarantee this. If you find that a cited link has gone
stale, use common sense and do

a phrase search with your favorite Web search engine. Where possible we
suggest ways to do this

near the URLs we cite.

Most abbreviations used in this book are expanded at first use. For
convenience, we have also

provided a glossary in an appendix.

References are usually by author name. Numbered footnotes are for URLs
that would intrude on

the text or that we suspect might be perishable; also for asides, war
stories, and jokes.2

To make this book more accessible to less technical readers, we invited
some non-programmers to

read it and identify terms that seemed both obscure and necessary to the
flow of exposition.

We

also use footnotes for definitions of elementary terms that an
experienced programmer is unlikely to

need.

Related References

Some famous papers and a few books by Unix’s early developers have mined
this territory before.

Kernighan and Pike’s *The Unix Programming Environment
*[*\[Kernighan-Pike84\] *](#532)stands out among

these and is rightly considered a classic. But today it shows its age a
bit; it doesn’t cover the Internet,

and the World Wide Web or the new wave of interpreted languages like
Perl, Tcl, and Python.

About halfway into the composition of this book, we learned of Mike
Gancarz’s *The Unix Philoso-*

*phy *[*\[Gancarz\]. *](#530)This book is excellent within its range,
but did not attempt to cover the full spectrum

of topics we felt needed to be addressed. Nevertheless we are grateful
to the author for the reminder

that the very simplest Unix design patterns have been the most
persistent and successful ones.

2 This particular footnote is dedicated to Terry Pratchett, whose use of
footnotes is quite...inspiring.

xix

Preface

*The Pragmatic Programmer *[*\[Hunt-Thomas\] *](#531)is a witty and wise
disquisition on good design practice

pitched at a slightly different level of the software-design craft (more
about coding, less about higher-

level partitioning of problems) than this book. The authors’ philosophy
is an outgrowth of Unix

experience, and it is an excellent complement to this book.

The Practice of Programming [*\[Kernighan-Pike99\] *](#532)*covers some
of the same ground as *The Prag-

*matic Programmer * from a position deep within the Unix tradition.

Finally (and with admitted intent to provoke) we recommend *Zen Flesh,
Zen Bones *[*\[Reps-Senzaki\], *](#535)

an important collection of Zen Buddhist primary sources.

References to Zen are scattered

throughout this book. They are included because Zen provides a
vocabulary for addressing some

ideas that turn out to be very important for software design but are
otherwise very difficult to hold in

the mind. Readers with religious attachments are invited to consider Zen
not as a religion but as a

therapeutic form of mental discipline — which, in its purest
non-theistic forms, is exactly what Zen

is.

Conventions Used in This Book

The term “UNIX” is technically and legally a trademark of The Open
Group, and should formally

be used only for operating systems which are certified to have passed
The Open Group’s elaborate

standards-conformance tests. In this book we use “Unix” in the looser
sense widely current among

programmers, to refer to any operating system (whether formally
Unix-branded or not) that is either

genetically descended from Bell Labs’s ancestral Unix code or written in
close imitation of its

descendants. In particular, Linux (from which we draw most of our
examples) is a Unix under

this definition.

This book employs the Unix manual page convention of tagging Unix
facilities with a following

manual section in parentheses, usually on first introduction when we
want to emphasize that this

is a Unix command. Thus, for example, read “munger(1)” as “the ‘munger’
program, which will

be documented in section 1 (user tools) of the Unix manual pages, if
it’s present on your system”.

Section 2 is C system calls, section 3 is C library calls, section 5 is
file formats and protocols, section

8 is system administration tools. Other sections vary among Unixes but
are not cited in this book.

For more, type **man 1 man **at your Unix shell prompt (older System V
Unixes may require **man -s**

1 man**). **

Sometimes we mention a Unix application (such as *Emacs*, without a
manual-section suffix and

capitalized.

This is a clue that the name actually represents a well-established
family of Unix

xx

Preface

programs with essentially the same function, and we are discussing
generic properties of all of

them. *Emacs*, for example, includes *xemacs*.

At various points later in this book we refer to ‘old school’ and ‘new
school’ methods.

As

with rap music, new-school starts about 1990.

In this context, it’s associated with the rise of

scripting languages, GUIs, open-source Unixes, and the Web.

Old-school refers to the pre-1990

(and especially pre-1985) world of expensive (shared) computers,
proprietary Unixes, scripting in

shell, and C everywhere. This difference is worth pointing out because
cheaper and less memory-

constrained machines have wrought some significant changes on the Unix
programming style.

Our Case Studies

A lot of books on programming rely on toy examples constructed
specifically to prove a point. This

one won’t. Our case studies will be real, pre-existing pieces of
software that are in production use

every day. Here are some of the major ones:

*cdrtools*/ *xcdroast*

These two separate projects are usually used together. The *cdrtools*

package is a set of CLI tools for writing CD-ROMs; Web search for

“cdrtools”. The *xcdroast * application is a GUI front end for cdrtools;

see the *xcdroast project site *\[http://www.xcdroast.org/\].

fetchmail

The *fetchmail * program retrieves mail from remote-mail servers using

the POP3 or IMAP post-office protocols. See the *fetchmail home page*

\[http://www.catb.org/\~esr/fetchmail\] (or search for “fetchmail” on
the

Web).

GIMP

The *GIMP *(GNU Image Manipulation Program) is a full-featured

paint, draw, and image-manipulation program that can edit a huge

variety of graphical formats in sophisticated ways. Sources are avail-

able from the *GIMP home page *\[http://www.gimp.org/\] (or search for

"GIMP" on the Web).

xxi

Preface

mutt

The *mutt * mail user agent is the current best-of-breed among text-

based Unix electronic mail agents, with notably good support for

MIME (Multipurpose Internet Mail Extensions) and the use of privacy

aids such as PGP (Pretty Good Privacy) and GPG (GNU Privacy

Guard).

Source code and executable binaries are available at the

*Mutt project site *\[http://www.mutt.org\].

xmlto

The *xmlto * command renders DocBook and other XML docu-

ments in various output formats, including HTML and text and

PostScript.

For sources and documentation, see the *xmlto project*

*site *\[http://cyberelk.net/tim/xmlto/\].

To minimize the amount of code the user needs to read to understand the
examples, we have tried

to choose case studies that can be used more than once, ideally to
illustrate several different design

principles and practices.

For this same reason, many of the examples are from my projects.

No

claim that these are the best possible ones is implied, merely that I
find them sufficiently familiar to

be useful for multiple expository purposes.

Author’s Acknowledgements

The guest contributors (Ken Arnold, Steven M. Bellovin, Stuart Feldman,
Jim Gettys, Steve Johnson,

Brian Kernighan, David Korn, Mike Lesk, Doug McIlroy, Marshall Kirk
McKusick, Keith Packard,

Henry Spencer, and Ken Thompson) added a great deal of value to this
book. Doug McIlroy, in

particular, went far beyond the call of duty in the thoroughness of his
critique and the depth of his

contributions, displaying the same care and dedication to excellence
which he brought to managing

the original Unix research group thirty years ago.

Special thanks go to Rob Landley and to my wife Catherine Raymond, both
of whom delivered

intensive line-by-line critiques of manuscript drafts.

Rob’s insightful and attentive commentary

actually inspired more than one entire chapter in the final manuscript,
and he had a lot to do with

its present organization and range; if he had written all the text he
pushed me to improve, I would

have to call him a co-author. Cathy was my test audience representing
non-technical readers; to the

extent this book is accessible to people who aren’t already programmers,
that’s largely her doing.

This book benefited from discussions with many other people over the
five years it took me to write

it. Mark M. Miller helped me achieve enlightenment about threads. John
Cowan supplied some

insights about interface design patterns and drafted the case studies of
*wily * and VM/CMS, and Jef

xxii

Preface

Raskin showed me where the Rule of Least Surprise comes from. The UIUC
System Architecture

Group contributed useful feedback on early chapters. The sections on
*What Unix Gets Wrong * and

*Flexibility in Depth * were directly inspired by their review. Russell
J. Nelson contributed the material

on Bernstein chaining in [*Chapter 7. *](#190)Jay Maynard contributed
most of the material in the MVS case

study in [Chapter 3. ](#78)

Les Hatton provided many helpful comments on the *Languages * chapter
and

motivated the portion of [*Chapter 4 *](#109)on *Optimal Module Size*.
David A. Wheeler contributed many

perceptive criticisms and some case-study material, especially in the
Design part. Russ Cox helped

develop the survey of Plan 9. Dennis Ritchie corrected me on some
historical points about C.

Hundreds of Unix programmers, far too many to list here, contributed
advice and comments during

the book’s public review period between January and June of 2003. As
always, I found the process

of open peer review over the Web both intensely challenging and
intensely rewarding.

Also as

always, responsibility for any errors in the resulting work remains my
own.

The expository style and some of the concerns of this book have been
influenced by the design

patterns movement; indeed, I flirted with the idea of titling the book
*Unix Design Patterns*. I didn’t,

because I disagree with some of the implicit central dogmas of the
movement and don’t feel the need

to use all its formal apparatus or accept its cultural baggage.
Nevertheless, my approach has certainly

been influenced by Christopher Alexander’s work3 (especially *The
Timeless Way of Building * and *A*

*Pattern Language*), and I owe the Gang of Four and other members of
their school a large debt of

gratitude for showing me how it is possible to use Alexander’s insights
to talk about software design

at a high level without merely uttering vague and useless generalities.
Interested readers should see

Design Patterns: Elements of Reusable Object-Oriented Software
[*\[GangOfFour\] *](#530)*for an introduction*

to design patterns.

The title of this book is, of course, a reference to Donald Knuth’s *The
Art of Computer Programming*.

While not specifically associated with the Unix tradition, Knuth has
been an influence on us all.

Editors with vision and imagination aren’t as common as they should be.
Mark Taub is one; he saw

merit in a stalled project and skillfully nudged me into finishing it.
Copy editors with a good ear

for prose style and enough ability to improve writing that isn’t like
theirs are even less common,

but Mary Lou Nohr makes that grade. Jerry Votta seized on my concept for
the cover and made it

look better than I had imagined. The whole crew at Addison-Wesley gets
high marks for making

the editorial and production process as painless as possible, and for
cheerfully accommodating my

control-freak tendencies not just over the text but deep into the
details of the book’s visual design,

art, and marketing.

3 An appreciation of Alexander’s work, with links to on-line versions of
significant portions, may be found at *Some Notes on*

*Christopher Alexander
*\[http://www.math.utsa.edu/sphere/salingar/Chris.text.html\].

xxiii
