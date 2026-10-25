# The finite lib: ways per component

**Lib v4**, seeded as v0 before any zip was read and grown since by merged batches (see the change log). It grows only as
[`_Rubric.md`](_Rubric.md) allows (a way must pass W1 to W4). Parameter values
never make a new way.

Each line: `` `id` `` | what it is | engine | Flouest.

- **engine**: `pdf` works in pdfLaTeX (and so in XeLaTeX and LuaLaTeX); `xe/lua`
  needs XeLaTeX or LuaLaTeX (Flouest's engine is pdfTeX); `ptex` needs the
  Japanese pTeX/e-pTeX engines (pLaTeX2e, DVI output), not pdfTeX.
- **Flouest**, what the repo's emitter has today: `P` a printer in
  `JSON->Latex Compiler/src/Packages/`; `G` General's output already uses it,
  with no printer of its own; `-` nothing yet. This column is what turns the
  research into a gap list.
- An id is `<component>.<way>`, lower case. A way carries no parameter in its
  id: `bib.bibtex-bst` is one way for every `.bst` style.

An analyser looks a component up here **before** proposing a way
(`grep -n 'thm\.' _Lib.md`). A proposal is written `NEW:<id>`.

## class: the document class (one way per distinct published class)

Classes are listed by family. A class brings a native vocabulary, noted after
the name. Any other published class is added as `class.<name>` with its profile.

| id | what it is | engine | Flouest |
|---|---|---|---|
| `class.article` | kernel article; `\maketitle`, `abstract` env | pdf | G |
| `class.report` | kernel report; `\chapter`, `titlepage` option | pdf | - |
| `class.book` | kernel book; `\frontmatter` `\mainmatter` `\backmatter`, `\chapter` | pdf | - |
| `class.letter` | kernel letter; `\opening` `\closing` | pdf | - |
| `class.scrartcl` | KOMA article; `\setkomafont`, `\KOMAoptions`, `\subject` `\publishers` | pdf | - |
| `class.scrreprt` | KOMA report | pdf | - |
| `class.scrbook` | KOMA book | pdf | - |
| `class.scrlttr2` | KOMA letter; `\LoadLetterOption`, `\setkomavar` | pdf | - |
| `class.memoir` | memoir; `\chapterstyle`, `\pagestyle`, `\setlrmarginsandblock` | pdf | - |
| `class.amsart` | AMS article; `\address` `\email` `\subjclass`, theorem styles | pdf | - |
| `class.amsbook` | AMS book | pdf | - |
| `class.beamer` | beamer; frames, `\usetheme`, overlays | pdf | - |
| `class.standalone` | standalone; crops to content | pdf | - |
| `class.tufte-handout` | Tufte handout; sidenotes, wide margins | pdf | - |
| `class.revtex4-2` | REVTeX; `\affiliation`, `\preprint` | pdf | - |
| `class.acmart` | ACM; `\ccsdesc`, `\keywords`, `\affiliation` | pdf | - |
| `class.ieeetran` | IEEEtran; `\IEEEauthorblockN`, `IEEEkeywords` | pdf | - |
| `class.elsarticle` | Elsevier; `frontmatter` env, `\ead`, `\address` | pdf | - |
| `class.llncs` | Springer LNCS; `\institute`, `\and`, `\keywords` | pdf | - |
| `class.moderncv` | CV class; `\cventry`, `\moderncvstyle` | pdf | - |
| `class.tikzposter` | poster class; blocks, `\usetheme` | pdf | - |
| `class.exam` | exam class; `questions`, `\points` | pdf | - |
| `class.flashcard` | `flashcard` (CTAN); two-sided question/answer cards `\flashcard[heading]{front}{back}`, `\flashcardtopic`, hooks `\flashcardformat` `\flashcardfrontword` `\flashcardbackword`; options `a4paper`, `centering` | pdf | - |
| `class.ulthese` | `ulthese` (CTAN; Université Laval thesis, memoir-based); `\titre` `\auteur` `\programme` `\direction`, `\frontispice`; options degree type and languages | pdf | - |
| `class.lebhart` | `lebhart` article class (CTAN); options `a4paper`/`b5paper`, `11pt`/`12pt`, `oneside`/`twoside`, `draft`/`fast`, `print`; other options go to `colorist` | xe/lua | - |
| `class.gsemthesis` | `gsemthesis` (CTAN; GSEM PhD thesis); options `fr` `draft` `custombib` `b5paper`, cover and front-matter commands | pdf | - |
| `class.ltxguide` | `ltxguide` (LaTeX base); documentation class of the LaTeX2e guides; `decl` environment, version-flag commands | pdf | - |
| `class.ltxdoc` | `ltxdoc` (LaTeX base); DocStrip `.dtx` driver class; `macrocode`/`macro` environments, `\DescribeMacro`, `\changes`, index and change history, `\DocInput` | pdf | - |
| `class.ucsmonograph` | `ucsmonograph` (CTAN; UCS/ABNT monograph on abntex2); `\imprimircapa` `\imprimirfolhaderosto` `\imprimirfolhadeaprovacao`, `resumo`, `dedicatoria`, `epigrafe`, `quadro`; options `12pt`, `oneside`/`twoside`, `cite=alf`/`num` | pdf | - |
| `class.abntex2` | `abntex2` (CTAN abnTeX2 bundle); ABNT academic work; options `chapter=TITLE`, `section=TITLE`, `openright`, `a4paper`, `ABNTEX*font` hooks | pdf | - |

## page: geometry and page-level layout

| id | what it is | engine | Flouest |
|---|---|---|---|
| `page.class-options` | paper and size set by class options (`a4paper`, `11pt`, `landscape`) | pdf | G |
| `page.geometry` | `geometry` package | pdf | - |
| `page.typearea` | KOMA `typearea` / `DIV`, `BCOR` | pdf | - |
| `page.memoir-layout` | memoir `\setlrmarginsandblock`, `\settypeblocksize` | pdf | - |
| `page.setlength` | raw `\setlength{\textwidth}`, `\oddsidemargin`, `\topmargin` | pdf | - |
| `page.vmargin` | legacy `vmargin`, `anysize`, `fullpage` | pdf | - |
| `page.a0poster` | `a0poster` large-format class options | pdf | - |
| `page.adjustwidth` | `changepage` `adjustwidth`/`adjustwidth*`: widens or indents a block into the margins by two lengths (KOMA `addmargin` is in `list.scrextend`) | pdf | - |
| `page.pdfscreen` | `pdfscreen` (CTAN, TeX Live; C. V. Radhakrishnan; extends `hyperref`): a screen-format page with an optional navigation side panel; options `screen` `rightpanel` `code` `paneltoc` `sectionbreak`, lengths `\panelwidth`, `\margins{..}`, `\screensize{w}{h}`, `\paneloverlay{file}` `\overlay{file}` (not `page.geometry`: paper size and margins only; a panel rebuilt by hand is bespoke; pdfTeX support is not stated on the CTAN page) | pdf | - |
| `cols.twocolumn-option` | class option `twocolumn` | pdf | - |
| `cols.twocolumn-cmd` | kernel `\twocolumn[...]` and `\onecolumn`: starts a two-column page with a full-width block above the columns (the argument is content; `\columnsep` and `\columnseprule` are lengths); the class option is `cols.twocolumn-option`, mid-page full-width material is `cols.cuted` | pdf | - |
| `cols.multicol` | `multicol` environment | pdf | P |
| `cols.paracol` | `paracol` parallel columns | pdf | - |
| `cols.vwcol` | `vwcol` (CTAN): `vwcol` environment, unequal-width text columns on one page that flow across pages; keys `widths` `sep` `rule` `indent` (`cols.multicol` is equal width, `cols.paracol` parallel text, `cols.minipage` fixed boxes) | pdf | - |
| `cols.cuted` | `cuted`/`stfloats` full-width material in two-column | pdf | - |
| `cols.balance` | `balance`: balances column heights on the last page of a two-column document (load-only switch) | pdf | - |
| `cols.minipage` | side-by-side `minipage`/`parbox` columns | pdf | - |
| `pg.break` | `\newpage`, `\pagebreak`, `\clearpage`, `\cleardoublepage` | pdf | G |
| `pg.flush` | `\flushbottom`, `\raggedbottom` | pdf | - |
| `pg.landscape` | `pdflscape`/`lscape` landscape pages | pdf | - |
| `pg.include-pdf` | `pdfpages` includes PDF pages | pdf | - |
| `pg.pgfpages` | `pgfpages` (PGF bundle): `\pgfpagesuselayout{layout}[keys]` and `\pgfpagesdeclarelayout{name}{defaults}{page options}` place logical pages on physical sheets (n-up, resize and centre, border shrink, paper-size keys); not `pg.landscape` (rotates pages) or `pg.include-pdf` (includes pages) | pdf | - |
| `pg.afterpage` | `afterpage`, `placeins` flow control | pdf | - |
| `pg.textpos` | `textpos` absolute positioning | pdf | - |
| `pg.emptypage` | `emptypage`: makes the blank pages inserted by `\cleardoublepage` truly empty (load-only switch) | pdf | - |
| `pg.needspace` | `needspace` `\needspace{len}`: page break unless that much vertical room remains | pdf | - |
| `pg.enlarge` | kernel `\enlargethispage{len}` and `\enlargethispage*{len}`: makes one page taller or shorter by a length so that it holds more or fewer lines (not `pg.break`, which ends pages; not `pg.needspace`, which asks for room; not `page.setlength`, which sets the global text block) | pdf | - |
| `pg.standalone-pkg` | `standalone` package (not `class.standalone`): `\usepackage[subpreambles,...]{standalone}` lets the main file `\input` sub-files that carry their own `\documentclass` and preamble, and `\includestandalone[options]{file}` includes a sub-file as source or image; options `subpreambles` `sort` `print` `comments` `group` `mode` `obeyclassoptions` `extension` `build` (`mode=build*` is **EXTERNAL** when selected) | pdf | - |

## hf: headers, footers, page numbers

| id | what it is | engine | Flouest |
|---|---|---|---|
| `hf.pagestyle-kernel` | `\pagestyle{plain,empty,headings,myheadings}`, `\thispagestyle` | pdf | - |
| `hf.fancyhdr` | `fancyhdr` | pdf | - |
| `hf.scrlayer-scrpage` | KOMA `scrlayer-scrpage` | pdf | - |
| `hf.memoir-pagestyle` | memoir `\makepagestyle` | pdf | - |
| `hf.titleps` | `titleps` | pdf | - |
| `hf.class-native` | a class's own running heads, set by its options/commands | pdf | - |
| `hf.extramarks` | `extramarks` (shipped in the `fancyhdr` distribution, TeX Live): `\extramarks{left}{right}` body marks read back by `\firstxmark` and `\lastxmark` in running head or foot fields (two plain strings per call, no options); used inside `hf.fancyhdr` fields | pdf | - |
| `pgnum.pagenumbering` | `\pagenumbering{arabic,roman,...}`, `\setcounter{page}` | pdf | - |
| `pgnum.lastpage` | `lastpage`/`totpages`/`zref-totpages` page X of Y | pdf | - |

## sp: spacing, text shape and typography

| id | what it is | engine | Flouest |
|---|---|---|---|
| `sp.setspace` | `setspace` (`\onehalfspacing`, `\setstretch`) | pdf | G |
| `sp.linespread` | `\linespread`, `\baselinestretch` | pdf | - |
| `sp.parskip-pkg` | `parskip` package | pdf | P |
| `sp.lengths` | raw `\parindent`, `\parskip`, `\itemsep`, `\topsep`..., and the paragraph-shape parameters `\hangindent` `\hangafter` (the `hang` package's `hangingpar` environment is a wrapper over them) | pdf | G |
| `sp.indentfirst` | `indentfirst` | pdf | - |
| `sp.ragged` | `ragged2e`, `\raggedright`, `\centering` | pdf | - |
| `sp.microtype` | `microtype` | pdf | - |
| `sp.hyphenat` | `hyphenat`, `\hyphenation`, `\sloppy` | pdf | - |
| `sp.draft-lineno` | `lineno` line numbers | pdf | - |
| `sp.rule` | kernel `\rule`, `\hrulefill`, `\dotfill`, and bare `\hrule`/`\vrule`/`\leaders` with a rule or dots only (the primitives the kernel's own fill-rules use); width, height, raise, colour via `xcolor`; leaders over arbitrary boxes are bespoke; a rule-drawing package is the parameter (`dashrule`: `\hdashrule[raise][colour]{width}{height}{dash pattern}`, a dashed rule) | pdf | - |
| `sp.manual-space` | kernel `\vspace`, `\addvspace`, `\hspace`, `\hfill`, `\raisebox`, `\\[len]`: manual spacing, filling, raising and line breaks, set by lengths | pdf | - |
| `sp.penalties` | integer penalty parameters `\widowpenalty`, `\clubpenalty`, `\brokenpenalty`, `\widowpenalties` (TeX/e-TeX parameters, as `sp.lengths` admits the raw length parameters); a widow and club control package is the parameter (`nowidow`: `\usepackage[all]{nowidow}` and per-paragraph `\nowidow[n]` `\noclub[n]`) | pdf | - |
| `sp.lettrine` | `lettrine` drop capitals `\lettrine[lines,lhang,loversize,findent,nindent,lraise]{C}{rest}` | pdf | - |
| `sp.frenchspacing` | kernel `\frenchspacing` / `\nonfrenchspacing`: on/off switch for the space after a period; one preamble line or a group wrapper (`sp.lengths` and `sp.penalties` are parameters, not this switch) | pdf | - |
| `sp.ellipsis` | `ellipsis` (CTAN): load-only fix for the uneven space around `\dots` in text mode; option `xspace` | pdf | - |
| `sp.selnolig` | `selnolig`: selectively suppresses typographic ligatures by search patterns; language option and rule lists (`sp.microtype` is protrusion and expansion, `font.fontspec` is face selection) | xe/lua | - |
| `sp.shapepar` | `shapepar` (CTAN, TeX Live; Donald Arseneau): `\shapepar{<shape>}` and predefined shapes such as `\heartpar{text}` set one paragraph inside a shape, scaling the text to fill it (not `sp.lengths`, which takes lengths; not `fig.wrapfig`, which wraps text round floats) | pdf | - |
| `sp.truncate` | `truncate` (CTAN, TeX Live; Donald Arseneau): `\usepackage[fit]{truncate}` and wrapper `\truncate{width}{text}` cut one line of text to a width and end it with a marker; used for running-head or caption fields (not `sp.hyphenat`, which breaks words) | pdf | - |

## font: typefaces and encodings

| id | what it is | engine | Flouest |
|---|---|---|---|
| `font.lmodern` | Latin Modern | pdf | G |
| `font.fontenc-t1` | `fontenc`, `inputenc`, `textcomp` | pdf | - |
| `font.newtx` | `newtxtext`+`newtxmath` (Times-like) | pdf | - |
| `font.mathptmx` | `mathptmx`/`times`/`tgtermes`/`txfonts` | pdf | - |
| `font.palatino` | `mathpazo`/`palatino`/`tgpagella` | pdf | - |
| `font.libertine` | `libertine`/`libertinus` | pdf | - |
| `font.charter` | `charter`/`XCharter` | pdf | - |
| `font.fourier` | `fourier`/`utopia` | pdf | - |
| `font.helvet` | `helvet`/`avant`/`tgheros`/`sfmath` sans | pdf | - |
| `font.mono` | `inconsolata`/`beramono`/`courier`/`sourcecodepro` | pdf | G |
| `font.family-default` | `\rmdefault`/`\sfdefault`/`\ttdefault`, `\renewcommand{\familydefault}` | pdf | - |
| `font.icons` | `fontawesome5`/`fontawesome` icons, and symbol-glyph packages whose commands print a pictogram or currency glyph (`marvosym`, `wasysym`, `eurosym`, `ifsym`, `pifont`), and `hologo` (CTAN), whose `\hologo{name}` prints a TeX-system logo by name; the package is the parameter | pdf | - |
| `font.fontspec` | `fontspec` `\setmainfont` | xe/lua | - |
| `font.unicode-math` | `unicode-math` | xe/lua | - |
| `font.size-commands` | `\small`..`\Huge`, `\fontsize{}{}\selectfont` | pdf | G |
| `font.display` | display, script or blackletter face packages whose switch sets the family for a span of text: `calligra` (`\calligra`), `yfonts`; the package is the parameter, as in `font.helvet` | pdf | - |
| `font.newunicodechar` | `newunicodechar` `\newunicodechar{char}{replacement}`: binds a Unicode character to a replacement that is a call into other lib ways (e.g. a `font.icons` command); any other replacement code is bespoke | pdf | - |
| `font.serif-pkg` | a serif text-face package whose family no other `font.*` line names (`sourceserifpro`, options `default,light`; `ebgaramond`, options `lf` `osf`); the package is the parameter, as `font.helvet` covers sans packages | pdf | - |
| `font.exscale` | `exscale` (LaTeX base): load-only switch that scales the Computer Modern math extension (cmex) fonts with the text size; no options (`font.size-commands` picks sizes, it does not scale cmex); `fix-cm` (LaTeX base) is the same type, a load-only switch that lets the Computer Modern fonts be used at any `\fontsize`, no options | pdf | - |
| `font.nfss` | LaTeX kernel NFSS: declare a family from font files (`\DeclareFontFamily`, `\DeclareFontShape`) and select any installed family for a span of text (`\usefont`, `\fontfamily`, `\fontencoding`) by encoding, family, series and shape names; global defaults stay in `font.family-default`, sizes in `font.size-commands` | pdf | - |

## color

| id | what it is | engine | Flouest |
|---|---|---|---|
| `color.xcolor` | `xcolor` (`\definecolor`, `\colorlet`, named sets) | pdf | P |
| `color.color` | legacy `color`, and `colordvi` (CTAN; named-colour text commands such as `\Red{...}`; the 0354 analysis records that its colour effect needs a dvips-compatible driver, **EXTERNAL** then); the package is the parameter | pdf | - |
| `color.pagecolor` | `\pagecolor`, page background colour | pdf | - |
| `color.transparent` | `transparent` `\transparent{value}`: opacity for text or boxes | pdf | - |

## bg: backgrounds, watermarks, decorations that reduce to a declarative way

| id | what it is | engine | Flouest |
|---|---|---|---|
| `bg.eso-pic` | `eso-pic` page overlay | pdf | - |
| `bg.background` | `background` package, and `wallpaper` (CTAN, built on `eso-pic`; page background pictures `\CenterWallPaper{scale}{file}` `\ThisCenterWallPaper{scale}{file}`, tiling variants); the package is the parameter | pdf | - |
| `bg.watermark` | `draftwatermark`/`xwatermark` | pdf | - |
| `bg.tikzpagenodes` | `tikzpagenodes` positioned overlay (**ART** when it draws the template's identity) | pdf | - |
| `bg.fancybox` | `fancybox` framed boxes and page frames | pdf | - |

## lang, meta, xref

| id | what it is | engine | Flouest |
|---|---|---|---|
| `lang.babel` | `babel`, and language-specific support packages loaded beside it (`polski` with options `MeX` `QX` `OT4` `T1`); the package is the parameter | pdf | - |
| `lang.polyglossia` | `polyglossia`, and language-specific XeLaTeX support packages (`xepersian`: Persian and mixed Persian-Latin text; options `localise` `fontsloadable`, font commands `\settextfont` `\setlatintextfont` `\defpersianfont`, the `\lr` span and `latin` environment, `\SepMark`, Persian-named aliases of kernel commands); the package is the parameter | xe/lua | - |
| `lang.csquotes` | `csquotes`, and `dirtytalk` (CTAN; `\say{text}` quotation marks with nested quotes); a quotation-mark package is the parameter | pdf | - |
| `lang.cjk` | `CJK`/`xeCJK`/`ctex` | xe/lua | - |
| `lang.projlib` | `projlib` `\UseLanguage{name}`: language, date and keyword names through one declarative command (pdfTeX support not established; seen under XeLaTeX/LuaLaTeX) | xe/lua | - |
| `lang.bidi` | `bidi`: right-to-left and left-to-right environments and `\RL{}` `\LR{}` direction switches for mixed-direction text | xe/lua | - |
| `lang.translator` | `translator` (beamer's keyword dictionary): `\newtranslation[to=<lang>]{<key>}{<text>}` per-language keyword and string translations (not `lang.babel` caption overrides, which use `\addto\captions<lang>`); `translations` (CTAN) is the same type, `\DeclareTranslation{Language}{key}{text}` and `\GetTranslation{key}`, the package is the parameter | pdf | - |
| `lang.ptex` | pTeX/e-pTeX Japanese typesetting parameters printed as preamble assignments (`\xspcode`, `\kanjiskip`, `\xkanjiskip`, `\prebreakpenalty`, `\postbreakpenalty`) under the pLaTeX2e format (`ptex-base`, CTAN and TeX Live); the values are integers, glue and penalties; not `lang.cjk` (CJK/xeCJK/ctex under XeLaTeX/LuaLaTeX) | ptex | - |
| `meta.hyperref` | `hyperref` options, `\hypersetup` | pdf | P |
| `meta.hyperxmp` | `hyperxmp` XMP metadata | pdf | - |
| `meta.bookmark` | `bookmark` | pdf | - |
| `meta.url` | `url`/`xurl` | pdf | - |
| `meta.pdfx` | `pdfx` PDF/A | pdf | - |
| `meta.glyphtounicode` | pdfTeX `\input{glyphtounicode}` and `\pdfgentounicode=1` (plus optional `\pdfglyphtounicode{name}{code}`): fills the PDF ToUnicode map so text copies and parses cleanly; a pdfTeX primitive and file, not XeTeX (not `meta.hyperxmp` XMP, `meta.pdfx` PDF/A or `meta.documentmetadata`); the `cmap` package (CTAN; load-only, placed before `fontenc`) reaches the same end for the 8-bit font encodings by supplying CMap resources, and is the parameter | pdf | - |
| `meta.accsupp` | `accsupp` (CTAN, LPPL 1.3c): `\usepackage{accsupp}` and the wrapper pair `\BeginAccSupp{ActualText={..}}` ... `\EndAccSupp{}` around a span; keys `ActualText` `Alt` `E` `Lang` take strings and replace the text a PDF reader extracts for the span (not `meta.glyphtounicode`, a per-glyph ToUnicode map; not `meta.hyperxmp`, XMP metadata) | pdf | - |
| `meta.documentmetadata` | kernel `\DocumentMetadata{...}` before `\documentclass` (`pdfstandard`, `tagging`, `lang`, `pdfversion`) plus `tagpdf` `\tagpdfsetup`; the `luamml` key is LuaLaTeX-only; not `meta.pdfx` | pdf | - |
| `meta.class-native` | a class's own PDF metadata and print-conformance commands (e.g. class `novel`: `\SetTitle` `\SetAuthor` `\SetPDFX[intent]{standard}`: strings, an output-intent name and a standard from a closed list); used where the class blocks `meta.pdfx` and `meta.hyperxmp` or disables the `meta.hyperref` metadata options; the engine follows the class (`novel` needs LuaLaTeX) | pdf | - |
| `xref.kernel` | `\label` `\ref` `\pageref` | pdf | G |
| `xref.hyperref` | `\autoref`, `\nameref`, `\hyperref` | pdf | P |
| `xref.cleveref` | `cleveref` | pdf | - |
| `xref.varioref` | `varioref` | pdf | - |
| `xref.zref` | `zref` | pdf | - |
| `xref.xr` | `xr` (CTAN, in TeX Live with `tools`; David Carlisle) and its hyperref-aware sibling `xr-hyper` (ctan.org/pkg/xr-hyper, part of the `hyperref` distribution): `\externaldocument[prefix][nocite]{file}` makes the labels of another document's `.aux` usable by `\ref` and `\cref`; the other document is built first (not `xref.kernel`, `xref.hyperref` or `xref.zref`, which refer within one document) | pdf | - |
| `xref.hypcap` | `hypcap` (CTAN, Heiko Oberdiek): load-only switch loaded after `hyperref`; options `all` `figure` `table` move the link anchor of a float to the top of the float instead of its caption (not `xref.hyperref`, the `\autoref` `\nameref` commands; not `meta.hyperref`, hyperref options) | pdf | - |

## front: title block, abstract, front matter

| id | what it is | engine | Flouest |
|---|---|---|---|
| `front.maketitle` | kernel `\title` `\author` `\date` `\maketitle` | pdf | G |
| `front.titling` | `titling` package restyles `\maketitle` | pdf | P |
| `front.authblk` | `authblk` `\author[1]` `\affil` | pdf | - |
| `front.titlepage-env` | `titlepage` environment hand-laid | pdf | - |
| `front.koma-title` | KOMA `\titlehead` `\subject` `\publishers` `\extratitle` | pdf | - |
| `front.class-native` | the class's own front-matter commands | pdf | - |
| `front.thanks` | `\thanks`, `\footnotemark` author notes | pdf | G |
| `abs.kernel` | `abstract` environment | pdf | G |
| `abs.abstract-pkg` | `abstract` package (`\abstractname`, `runin`) | pdf | P |
| `abs.class-native` | the class's own abstract environment or command | pdf | - |
| `abs.keywords` | keyword line (class command, or `\par\textbf{Keywords}`) | pdf | - |
| `abs.classification` | CCS, MSC, PACS, JEL codes (class command) | pdf | - |
| `front.dedication` | dedication/declaration/copyright/acknowledgement pages | pdf | G |
| `front.datetime` | `datetime`/`datetime2` date formats: `\newdateformat{name}{...}`, printed with `\name\today`; also `datemultical` (CTAN): named dates printed in a chosen calendar, `\dmcset{name}{y}{m}{d}`, `\dmc[cal]{name}{style}`, `\dmcstyle` patterns, options `native` `persian` (its Lua backend for the 54 calendars needs LuaLaTeX; `gr` `sh` `lh` work in pdfLaTeX); the package is the parameter | pdf | - |
| `front.doclicense` | `doclicense`: licence text and icon for a copyright page; options type, modifier, version, holder | pdf | - |
| `front.aidisclose` | `aidisclose` (CTAN): an AI-use declaration for a thesis or paper; options `autobib` `nocite`, preamble `\AIDactivate{key}` selections and `\AIDtoolsUsed`, body `\AIDrenderDeclaration[ncols=n]{name}` | pdf | - |
| `front.hep-title` | `hep-title` (CTAN; builds on `titling` and `authblk`): title-page extensions for preprints; `\series` `\subtitle` `\editor[labels]{}` `\endorser[label]{}` `\affiliation[label]{}` `\email` `\thanks[label]`, corner blocks `\preprint` `\arxiv` `\doi` `\reprint`; font switches and pre/post hooks per field; no package options | pdf | - |
| `front.titlepic` | `titlepic`: adds a `\titlepic{...}` picture slot to the kernel `\maketitle` (the one argument is content, an image); `\usepackage{titlepic}` | pdf | - |
| `front.uni-titlepage` | `uni-titlepage` (CTAN, LPPL 1.3c, Markus Kohm; builds on KOMA `scrbase`): `\usepackage{uni-titlepage}`, `\TitlePageStyle[keys]{Style}` (the style is one of 13 names from a closed list, a parameter), `\maketitle[key=value]`, `\TitleOptions{..}`, string keys for the title elements, style options `rulewidth` `rulesep` `rulecolor` `blackborder` `final` `extratitle` `uppertitleback` `lowertitleback`, environments `titlepage` and `fullsizetitle`; replaces the kernel `\maketitle` while loaded; a package that serves the title page of any thesis or book, not a class and not one university (a sibling of `front.hep-title`; not `front.titling`, which restyles `\maketitle` by hooks; not `front.koma-title`, which sets fields) | pdf | - |
| `toc.kernel` | `\tableofcontents` `\listoffigures` `\listoftables` | pdf | G |
| `toc.tocloft` | `tocloft` | pdf | P |
| `toc.titletoc` | `titletoc` | pdf | - |
| `toc.koma` | KOMA toc options (`toc=...`) | pdf | - |
| `toc.etoc` | `etoc`/`minitoc`/`tocbibind`, and other contents-list packages (`multitoc`: the contents in columns, load option `toc`); the package is the parameter | pdf | - |
| `toc.tocbasic` | KOMA `tocbasic` `\DeclareNewTOC`, `\setuptoc`, `\DeclareTOCStyleEntries`: new list-of/float types and toc entry styles | pdf | - |

## head: sectioning

| id | what it is | engine | Flouest |
|---|---|---|---|
| `head.kernel` | `\section` etc. with `\renewcommand` of counters/format | pdf | G |
| `head.titlesec` | `titlesec` `\titleformat` `\titlespacing` | pdf | P |
| `head.sectsty` | `sectsty` | pdf | - |
| `head.koma-fonts` | KOMA `\setkomafont{section}`, `\addtokomafont` | pdf | - |
| `head.memoir-style` | memoir `\chapterstyle`, `\setsecheadstyle` | pdf | - |
| `head.fncychap` | `fncychap` chapter styles | pdf | - |
| `head.class-native` | the class's own heading looks, set by options | pdf | - |
| `num.secnumdepth` | `secnumdepth`, `tocdepth` counters | pdf | G |
| `num.counters` | `\setcounter`, `\numberwithin`, `chngcntr`, `\renewcommand\the...`, and a package that changes how every counter prints (`dozenal`: base twelve, `\usepackage[typeone]{dozenal}`, glyph digits `\x` `\e`) | pdf | G |
| `num.appendix` | `\appendix`, `appendix` package | pdf | G |

## list, quote, marks, notes

| id | what it is | engine | Flouest |
|---|---|---|---|
| `list.kernel` | `itemize` `enumerate` `description` | pdf | G |
| `list.enumitem` | `enumitem` | pdf | P |
| `list.paralist` | `paralist`/`mdwlist`/`tasks` | pdf | - |
| `list.enumerate-pkg` | `enumerate` (tools bundle): label template in the optional argument, e.g. `[{State} A:]` | pdf | - |
| `list.scrextend` | KOMA `scrextend`: `labeling` list and `addmargin` indented-block environments | pdf | - |
| `quote.kernel` | `quote` `quotation` `verse` | pdf | - |
| `quote.epigraph` | `epigraph` | pdf | - |
| `quote.verse-pkg` | `verse` package (Peter Wilson): extends the kernel `verse` environment with `\poemtitle`, `\flagverse`, `\versewidth`, set by lengths and font hooks (separate from `quote.kernel` as `list.enumerate-pkg` is from `list.kernel`) | pdf | - |
| `quote.dialogue` | `dialogue` package: `dialogue` environment with `\speak{name}` for scripts and interviews | pdf | - |
| `mark.kernel` | `\textbf` `\emph` `\textsc` `\textsf` | pdf | G |
| `mark.case` | kernel `\MakeUppercase` `\MakeLowercase` (and `\uppercase` `\lowercase`) and the `textcase` package's `\MakeTextUppercase` `\MakeTextLowercase`: wrap a span of text and change its case (not `mark.kernel`, which is font switches only) | pdf | - |
| `mark.ulem` | `ulem`/`soul` underline, strike, highlight | pdf | G |
| `mark.siunitx` | `siunitx` units and numbers, and `numprint` (CTAN; `\usepackage[autolanguage]{numprint}` and inline `\numprint{1100}`: thousands separators by language); the number-printing package is the parameter (not `mark.numspell`, words; not `mark.nth`, ordinals) | pdf | - |
| `mark.contour` | `contour` (CTAN): coloured outline around inline text; `\usepackage[outline]{contour}`, `\contourlength{len}`, wrapper `\contour{colour}{text}` (not `mark.ulem`: underline, strike, highlight) | pdf | - |
| `mark.numspell` | `numspell` (CTAN): cardinal and ordinal numbers spelled out in words (English, French, German, Hungarian, Italian, Latin), inline commands such as `\Ordnumspell{n}`; the language is a parameter (not `mark.nth`: numeral plus ordinal suffix) | pdf | - |
| `mark.nth` | `nth`: English ordinals, `\usepackage[super]{nth}` and inline `\nth{n}` | pdf | - |
| `mark.menukeys` | `menukeys`: inline keyboard-key, menu-path and directory-path markup `\keys{}` `\menu{}` `\directory{}`; `os` option and preset styles chosen with `\renewmenumacro` | pdf | - |
| `fn.kernel` | `\footnote` | pdf | G |
| `fn.footmisc` | `footmisc`, and other footnote-layout packages (`dblfnote`, in the `yafoot` bundle: the footnotes of a single-column text set in two columns, length `\DFNcolumnsep`); the package is the parameter | pdf | P |
| `fn.endnotes` | `endnotes` | pdf | - |
| `fn.bigfoot` | `bigfoot`/`manyfoot`/`footnotehyper` | pdf | G |
| `fn.footnotebackref` | `footnotebackref`: back-links from footnotes to the text (load-only switch, loaded after `hyperref`) | pdf | - |
| `fn.fixfoot` | `fixfoot` (CTAN, TeX Live; David Carlisle, Robin Fairbairns): `\DeclareFixedFootnote{\cmd}[n]{text}` declares a command that prints one footnote text, once per page, wherever it is used (not `fn.kernel`, one `\footnote` per use; not `fn.bigfoot`) | pdf | - |
| `note.marginnote` | `marginnote` | pdf | P |
| `note.marginpar` | kernel `\marginpar` | pdf | - |
| `note.sidenotes` | `sidenotes`/Tufte sidenotes | pdf | - |
| `note.todonotes` | `todonotes` | pdf | - |
| `note.notecolumn` | KOMA `scrlayer-notecolumn`: named side-note columns `\DeclareNewNoteColumn`, `\makenote`, `\syncwithnotecolumn` | pdf | - |
| `note.mparhack` | `mparhack`: load-only fix for the side and placement of margin notes (`\marginpar`) | pdf | - |

## math and theorem-like statements

| id | what it is | engine | Flouest |
|---|---|---|---|
| `math.amsmath` | `amsmath` `align`, `\numberwithin` | pdf | G |
| `math.mathtools` | `mathtools` | pdf | P |
| `math.amssymb` | `amssymb`/`amsfonts` | pdf | G |
| `math.bm` | `bm`/`mathrsfs`/`dsfont`/`mathbbol` | pdf | - |
| `math.physics` | `physics`/`braket`/`cancel`/`nccmath`/`empheq` | pdf | G |
| `math.eqnumber` | `leqno`, `fleqn`, equation numbering style | pdf | - |
| `math.kernel` | kernel display maths without `amsmath`: `equation`, `eqnarray`, `displaymath`, `\[ \]`, `\nonumber`; numbering through counters and `\theequation` (`leqno`/`fleqn` stay in `math.eqnumber`) | pdf | - |
| `math.icomma` | `icomma`: intelligent comma in maths (decimal comma that is also a list separator); load-only | pdf | - |
| `math.nicefrac` | `nicefrac` (distributed with the `units` bundle): `\nicefrac[font]{1}{2}` inline slash fractions; also `xfrac` (CTAN, l3packages): `\sfrac[..]{1}{2}`, instances set with `\DeclareInstance`; the package is the parameter | pdf | - |
| `math.subdepth` | `subdepth` (CTAN, Will Robertson, LPPL 1.3c): load-only fix that gives subscripts the same depth with or without a superscript; no options (a load-only switch, as `math.icomma`) | pdf | - |
| `math.mleftright` | `mleftright` (CTAN, LPPL 1.3): `\mleft` and `\mright`, variants of `\left` and `\right` whose delimiters act as `\mathopen` and `\mathclose`, so no extra space appears inside; one load line, no options listed on the CTAN page (not `math.mathtools`, whose `\DeclarePairedDelimiter` is another command) | pdf | - |
| `thm.kernel` | kernel `\newtheorem` | pdf | - |
| `thm.amsthm` | `amsthm` `\theoremstyle`, `\newtheoremstyle` | pdf | P |
| `thm.ntheorem` | `ntheorem` | pdf | - |
| `thm.thmtools` | `thmtools` | pdf | - |
| `thm.tcolorbox` | `tcolorbox` theorems library | pdf | P |
| `thm.mdframed` | `mdframed`/`framed` around theorems | pdf | - |
| `thm.class-native` | theorem styles and names set by the class | pdf | - |
| `alg.algorithm2e` | `algorithm2e` | pdf | - |
| `alg.algorithmicx` | `algorithm`+`algpseudocode`/`algorithmic` | pdf | - |

## fig, tbl, cap: floats

| id | what it is | engine | Flouest |
|---|---|---|---|
| `fig.graphicx` | `figure` float + `\includegraphics` | pdf | G |
| `fig.float` | `float` `[H]`, `\newfloat` | pdf | G |
| `fig.newfloat` | `newfloat` `\DeclareFloatingEnvironment[options]{name}`: new float types (placement, name, within); the `float` package's `\newfloat` is `fig.float` | pdf | - |
| `fig.svg` | `svg` (CTAN): `\includesvg[width=..]{file}` and `\includeinkscape`; per-image keys (**EXTERNAL**: runs the Inkscape command line, as `code.minted` runs pygments; `fig.graphicx` takes no SVG) | pdf | - |
| `fig.epstopdf` | `epstopdf` (CTAN, TeX Live; the LaTeX package is `epstopdf-pkg`): `\usepackage{epstopdf}` and `\epstopdfsetup{...}` keys let `\includegraphics` take `.eps` files under pdfTeX by converting them with Ghostscript (**EXTERNAL** when an EPS file is included, as `fig.svg` runs Inkscape; `fig.graphicx` takes no EPS under pdfTeX without a converter) | pdf | - |
| `fig.subcaption` | `subcaption`/`subfig`/`subfigure` | pdf | - |
| `fig.wrapfig` | `wrapfig` | pdf | - |
| `fig.floatrow` | `floatrow`/`sidecap` | pdf | - |
| `fig.adjustbox` | `adjustbox` | pdf | P |
| `fig.rotating` | `rotating`/`graphicx` rotation | pdf | G |
| `fig.placement` | `placeins`/float placement parameters | pdf | - |
| `fig.class-native` | a class's own image-cell containers and macros, set by arguments (e.g. class `photobook`: `\begin{inlinecell}{width}{height}`, `\imagecell[fill]{}{image}`); parallel to `thm.class-native`, `front.class-native`, `head.class-native` | pdf | - |
| `tbl.tabular` | kernel `tabular` + `array` | pdf | P |
| `tbl.tabularx` | `tabularx`/`tabulary` | pdf | G |
| `tbl.longtable` | `longtable`/`xltabular`/`supertabular` | pdf | - |
| `tbl.booktabs` | `booktabs` | pdf | P |
| `tbl.colortbl` | `colortbl`/`xcolor[table]` | pdf | P |
| `tbl.arydshln` | `arydshln` (CTAN): dashed rules in `array`/`tabular`: `\hdashline[dash/gap]`, `\cdashline{a-b}` and the column separator `;{dash/gap}`; the dash and gap lengths are the parameters (a rule package of its own, as `tbl.booktabs` and `tbl.colortbl`) | pdf | - |
| `tbl.multirow` | `multirow`/`makecell`/`diagbox` | pdf | G |
| `tbl.threeparttable` | `threeparttable`/table notes | pdf | - |
| `tbl.siunitx` | `siunitx` `S` columns, `dcolumn` | pdf | - |
| `tbl.nicematrix` | `nicematrix`/`tabu`/`tabularray` (key-value `tblr` specification, `\UseTblrLibrary`); the package is the parameter | pdf | - |
| `tbl.calctab` | `calctab` (CTAN; needs `fltpoint`): `xcalctab` environment of amount rows `\amount[id=]{label}{qty}{price}`, `\add[id=,refs]{label}`, `\perc[id=,ref]{label}{percent}` with sums and percentages computed in TeX; header and currency strings `\ctdescription` `\ctheaderone` `\ctheadertwo` `\ctcurrency`, rounding `\nprounddigits` (not `tbl.tabular`: hand-set columns; not `tbl.siunitx`: alignment only) | pdf | - |
| `cap.kernel` | kernel `\caption` | pdf | G |
| `cap.caption` | `caption` package | pdf | P |
| `cap.koma` | KOMA caption options | pdf | - |
| `cap.memoir` | memoir/`ccaption` | pdf | - |

## code and boxes

| id | what it is | engine | Flouest |
|---|---|---|---|
| `code.verbatim` | `verbatim`, `\verb`, `fancyvrb`, `alltt` | pdf | - |
| `code.listings` | `listings` | pdf | P |
| `code.upquote` | `upquote` (CTAN): load-only switch, no options; `\verb` and verbatim print `'` and `` ` `` as upright quote glyphs (a separate package from `code.verbatim`, as `fn.footnotebackref` is from `fn.kernel`) | pdf | - |
| `code.minted` | `minted` (**EXTERNAL**: shell escape and pygments), and `pygmentex` (CTAN; `pygmented` environment, `lang=` key; **EXTERNAL**: a Python Pygments pass); the package is the parameter | pdf | - |
| `code.tcblisting` | `tcolorbox` listings library | pdf | P |
| `box.tcolorbox` | `tcolorbox` | pdf | P |
| `box.mdframed` | `mdframed`/`framed`/`shaded` | pdf | - |
| `box.fancybox` | `fancybox`/`\fbox`/`\fcolorbox`/`boites` | pdf | - |
| `box.minipage` | `minipage`/`\parbox` | pdf | - |
| `box.eqparbox` | `eqparbox` (CTAN): boxes that take the width of the widest box with the same tag: `\eqparbox[pos][height][inner]{tag}{text}`, `\eqmakebox[tag][align]{text}`, `\eqboxwidth{tag}`; width is read back from the aux file, so two passes (not `box.minipage`, whose width is given) | pdf | - |
| `box.stackengine` | `stackengine`: stack or overlay one object on another with gap and alignment (`\stackon`, `\stackunder`, `\stackinset`, `\setstackgap`) | pdf | - |

## bib: bibliography and index

| id | what it is | engine | Flouest |
|---|---|---|---|
| `bib.thebibliography` | hand-written `thebibliography` | pdf | - |
| `bib.bibtex-bst` | BibTeX with a `.bst` style (the style is a parameter) | pdf | - |
| `bib.natbib` | `natbib` citation commands and options | pdf | - |
| `bib.biblatex-biber` | `biblatex` with biber | pdf | - |
| `bib.biblatex-bibtex` | `biblatex` with the bibtex backend | pdf | P |
| `bib.cite-pkg` | `cite` package ordering, and load-only citation-run packages (`breakcites`: a run of citations may break at the line end, no options); the package is the parameter | pdf | - |
| `bib.apacite` | `apacite`/`chicago`/`harvard`/`jurabib` | pdf | - |
| `bib.multi` | `multibib`/`bibunits`/`chapterbib`/`refsection` | pdf | - |
| `idx.makeidx` | `makeidx`/`imakeidx`/`index`, and `idxcmds` (CTAN; `\newidxcmd\name{format}[suffix]` declares a command that prints its text and writes an index entry); the package is the parameter | pdf | - |
| `idx.glossaries` | `glossaries`/`nomencl`/`acronym` | pdf | - |

## doc-kind specific (one way per package family)

| id | what it is | engine | Flouest |
|---|---|---|---|
| `slide.beamer-theme` | `\usetheme`/`\usecolortheme`/`\usefonttheme`/`\useinnertheme`/`\useoutertheme` (theme name is a parameter) | pdf | - |
| `slide.beamer-template` | `\setbeamertemplate`, `\setbeamercolor`, `\setbeamerfont`, and the template names that an add-on package supplies (`beamer-varbox`: `\setbeamertemplate{block begin}[variable rounded][cornerpercent,shadow,width]` after `\usepackage[cornerpercent=..]{beamer-varbox}`); the package is the parameter | pdf | - |
| `slide.beamer-mode` | handout, notes, overlays (`\only`, `\pause`) | pdf | - |
| `slide.beamer-section-hook` | beamer `\AtBeginSection[]{...}` / `\AtBeginSubsection[]{...}`: per-section frame hook; body limited to a frame of declarative beamer commands (`\tableofcontents[...]`, `\sectionpage`) | pdf | - |
| `poster.tikzposter` | `tikzposter` blocks and themes | pdf | - |
| `poster.baposter` | `baposter`/`beamerposter` | pdf | - |
| `ltr.opening` | letter commands and letterhead (kernel/KOMA/`newlfm`) | pdf | - |
| `ltr.envlab` | `envlab`: envelopes and mailing-label sheets for letter-compatible classes; options plus `\SetEnvelope` `\SetLabel` `\SetBigLabel` `\makelabels` (dvips-oriented page model, pdfTeX unverified) | pdf | - |
| `cv.entries` | CV class entry commands (moderncv/altacv/awesome-cv family) | pdf | - |
| `cv.timeline` | `moderntimeline`: date-range timeline bar on moderncv entries, `\tlcventry` `\tllabelcventry` `\tldatecventry` `\tldatelabelcventry`; options `firstyear` `lastyear` `marksyr` `marksmo` | pdf | - |
| `exam.questions` | `exam`/`examdesign` question environments, and other question-bank packages (`esami`: seeded variants, shuffled answers, per-version numbers; `mcexam`: multiple-choice tests with `mcquestions` and `mcanswerslist`, randomised versions, `output=` modes, its `analysis` mode **EXTERNAL** (R) when selected); the package is the parameter | pdf | - |
| `draft.todo` | `todonotes`/`changes`/`showframe` review aids, and `lipsum` dummy paragraphs (`\lipsum[range]`, `\setlipsum`; the text is filler content), and `anonymous-acm` (CTAN; double-blind switch for `acmart`: `\usepackage[true]{anonymous-acm}` (or `false`) and wrappers `\authoranon` `\textanon` `\linkanon` `\textlinkanon` `\citeanon`); the package is the parameter | pdf | - |
| `ticket.sheet` | `ticket`: imposed sheet of tickets, labels and cards; options `boxed` `cutmark`, `\ticketNumbers` `\ticketSize` `\ticketDistance`, body `\ticket{...}` per ticket (the ticket face is outside the way: content, or ART when it draws the template's identity) | pdf | - |
| `legal.contract` | `contract` / KOMA `scrjura`: numbered legal clauses, `contract` environment, `\Clause[title]`, `\setkeys{contract}`, `contract.Clause` font element | pdf | - |
| `exam.schooldocs` | `schooldocs`: named page styles over `fancyhdr` (`classic` `elegant` `modern` `soft` `exam` `collection` `identity`), a redefined `\maketitle` with `\makesmalltitle`, `\seprule`, `\correct`, `\subtitle`, a default geometry; tuned by lengths, colours, font-switch lists and the string `\titleflush` (school sheets, exams, course notes) | pdf | - |
| `exam.rtl-questions` | `exam-rtl`: typed `Question` wrapper with `MC` `TF` `FillBlank` `Ordering` `Matching` `Essay` `ShortAnswer` `ReadingPassage` environments, student/teacher mode switches, `ExamID` seed and answer-key boxes; Arabic labels fixed in the package; a way apart from `exam.questions` because it needs XeLaTeX or LuaLaTeX | xe/lua | - |
| `label.flabels` | `flabels`: ring-binder spine labels; options `leitz` `fullheight` `narrow` `color` `a4paper` `nice` `nohole`, `\company`, `\setbgcompany` `\setfgcompany` `\setbglabel` `\setfglabel`, lengths `\labeltextmargin` `\hspaceinterlabel` `\extratopmargin`, body `\emptylabel{n}` and `\labeltext{text}` (not `ltr.envlab` envelopes and mailing labels, not `ticket.sheet`) | pdf | - |
| `inv.simpleinvoice` | `simpleinvoice`: a whole invoice (title, parties, item rows, totals, bank line) from `\set...` string commands, `\additem` rows and one `\makeinvoice` | pdf | - |
| `notebook.ftc` | `ftc-notebook`: FIRST Tech Challenge engineering/outreach notebook; options `Num` `Name` `Logo` `Notebook` `KindOne`..`KindSix` `Grid` `Green`/`Orange`/`Blue`; body `CoverPage`, `ListOfTasks`, `StartNotebook`, `Month`, `TeamStory`, `Bio`, `Meeting`/`TaskInfo`/`Task`, `Section`, `DescriptionTable`/`DecisionTable`, `PictFigure`/`ExplainedPictFigure`/`GroupedFigures` | pdf | - |
| `cal.kalender` | `kalender` (CTAN): `\usepackage{kalender}` and body `\Kalender{<year>}`, a one-page German year-at-a-glance grid; the year is the only value, the German names and the grid are fixed | pdf | - |
| `ltr.formlett` | `formlett` (CTAN, TeX Live): mail merge; one letter body between `\beginletter` and `\endletter` with `\paras[n][m]` / `\blockparas[n]` placeholders, rendered once per `\moreletter` data record (`;` fields, `+` sub-groups, `!` terminator); `\NOPAGENUMBERS` and a `\preview` debug switch (not `ltr.opening`, `ltr.envlab` or `ticket.sheet`) | pdf | - |
| `poster.modernposter` | `modernposter` class (extends `a0poster`): `postercolumn`, `\posterbox[height]{title}{content}`, `\doubleposterbox[fraction]{t1}{c1}{t2}{c2}`, `\highlight`; class options `hlcolor` `logo` `helvet` | pdf | - |
| `poster.tcbposter` | `tcolorbox` poster library: `tcbposter` environment and `\posterbox[..]{..}{..}`; the grid and boxes are key=value options (`poster={columns,rows,spacing}`, `boxes`, per box `name` `column` `span` `rowspan` `below` `colback` `halign` `valign`...); not `box.tcolorbox` (one box) | pdf | - |
| `dtx.doc` | `doc` (LaTeX base `doc.sty`) under any class: typesets DocStrip `.dtx` sources with `\DocInput{file.dtx}`, `macrocode`/`macro` environments, `\GetFileInfo`, `\changes`, `\StopEventually`/`\Finale`, `\MakeShortVerb`; options and switches `multicol`, `\RecordChanges`, `\CodelineNumbered`, `\EnableCrossrefs`, `\DoNotIndex`; `class.ltxdoc` is the class that loads this same package; other package-documentation packages are the parameter (`hypdoc`: load-only hypertext features for a `doc` manual; `codedescribe`: `\usepackage[infograb]{codedescribe}` with `\tstitle` and the `codedescribe` and `describelist` environments, for a plain `.tex` manual) | pdf | - |
| `slide.pdfpc-movie` | `pdfpc-movie` (CTAN): `\pdfpcmovie[keys]{poster material}{movie file}` makes the poster material a link to a movie for the PDF Presenter Console; keys `width` `height` `depth` (dimensions), flags `autostart` `loop` `noprogress`, integer-second `start` `stop`; the movie file is a shipped asset | pdf | - |
| `slide.colourchange` | `colourchange` (CTAN, GPL): beamer add-on that moves the structure colour from one colour to another over the slides or frames, or sets it by hand; options `slidechange` `framechange` `draft` `defaultstyle` `final`, preamble `\selectcolourchanges{first}{second}`, body `\selectmanualcolour{colour}` between frames; needs two compiles (`slide.beamer-template` sets a static colour) | pdf | - |
| `slide.texpower` | `texpower` (CTAN, TeX Live; Stephan Lehmke, Hans Fredrik Nordhaug; GPL): dynamic-presentation overlays for a slide class such as `foiltex` or `seminar`, or for the `pdfslide` package (beamer overlays are `slide.beamer-mode`); option `display`, body wrappers `\step{}` `\stepwise{}` `\parstepwise{}` `\restep{}` `\switch{}{}`; pdfTeX support is not stated on the CTAN page | pdf | - |
| `slide.hackthefootline` | `hackthefootline` (CTAN beamer-contrib, LPPL 1.3c): a beamer footline chosen by `\usepackage[twocols,countappendixframes,nofun]{hackthefootline}` (column options `onecol` `twocols` `threecols`) and `\htfconfig{cols,title,authinst,date,framenrs,atsep}`, callable in the preamble or between frames (not `slide.beamer-template`, whose `\setbeamertemplate{footline}{..}` takes free box code; not `slide.beamer-theme`, a whole outer theme) | pdf | - |
| `slide.beamersubframe` | `beamersubframe` (CTAN beamer-contrib, v0.2, LPPL): moves flagged frames to the end of the PDF or keeps them in place; options `embed` `append` `nominiframes`, body `subframe[opts]{title}` and `lastframe` environments, `\appendsubframes` before `\end{document}`, conditionals `\ifappend{}{}` `\ifsubframe{}{}`; needs two runs (not `slide.beamer-mode`, overlays; not `slide.colourchange`, colour) | pdf | - |
| `ltr.envelope-letter` | `envelope-letter` (CTAN): `\usepackage{envelope-letter}` and body `\makeenvelope[options]` right after `\begin{letter}` adds one borderless first page with fold lines, step marks, scissors marks, recipient and sender addresses and an optional `\setstamp`; pgfkeys options (`grammage`, `to`, `from`, line and step modes), `\envelopesetup{}`; serves any letter-compatible class (not `ltr.envlab`: envelopes and label sheets with `\SetEnvelope`; not `ltr.opening`) | pdf | - |
| `logbook.dmlb` | `diabetes-logbook` (CTAN; files `dmlb.*`): a whole diabetes logbook; option `graph` (**EXTERNAL** when selected: the graph pass needs shell escape), colour names, `\edef` strings and lengths `\mym` `\myd` `\myRelPath`, body `\dmlbsetdate{Y}{M}{D}` and one `\QQQ{time}{BG}{Ins}{CHO}{Pro}{Fat}{remarks}` row per entry (the row offset and the `yy-mm.tex` file naming are fixed in the package) | pdf | - |
| `struct.simplesystemtex` | `simplesystemtex` (CTAN): a multi-file document engine; `\ImportSection{path}(name)` imports section files in order into a path-derived group tree, `\AddPart{name}`, a generated `\TableofContents`, typed blocks `\NewBlockType{Name}` looked up by `\SetStyle{Type}{code}` style slots, cross-links `\seclink` `\blclink` `\indlink`, block indexes `\MakeBlockIndex{scope/}`, switch `\AutomaticListon`; the emitter writes one `.tex` file per section; the package's own logo and cover commands brand one project and are outside the way | pdf | - |
| `inv.facture-belge` | `facture-belge-simple-sans-tva` (CTAN): a Belgian invoice or expense note for an individual, from string commands: `\rsNoDate{no}{date}`, address-table commands `\rsEnteteTableauAdresses` `\rsLigneTableauAdresses`, an `xcalctab` product table (`tbl.calctab`), `\rsCompteBancaireEtDateLimiteDePaiement{iban}{date}`, and the expense-note commands `\rsIdentificationCreancier` ... `\rsLigneTableauItemsARembourser`; options are babel language names and `latin1`; loads `fontspec` unconditionally (a sibling of `inv.simpleinvoice`, a different package) | xe/lua | - |
| `card.gcard` | `gcard` (CTAN, TeX Live, LPPL; George McBane): one folded greeting card; `\usepackage{gcard}`, lengths `\gcguttermargin` `\gcedgemargin` `\gctopmargin` `\gcbottommargin`, and four panel environments `frontcover` `insideleft` `insideright` `backcover` (the CTAN page names `textpos` and `graphicx` as dependencies and says panels are set in minipages; the source was not read; not `ticket.sheet`, many tickets per sheet; not `pg.pgfpages`, n-up of logical pages; not `class.flashcard`) | pdf | - |
| `cal.termcal` | `termcal` (CTAN, TeX Live, LPPL): `\usepackage{termcal}` and a body `calendar` environment, a course or academic-term calendar of weeks; the start date, the number of weeks, weekday names, per-day option macros, date-keyed text and the length `\calboxdepth` are the values (not `cal.kalender`, a fixed German year grid with one parameter) | pdf | - |
| `report.practicalreports` | `practicalreports` (CTAN, TeX Live, MiKTeX, LPPL 1.3c; Justin Cawood): a science practical (lab) report; `\usepackage{practicalreports}`, `\setpagefancy` `\header{l}{c}{r}` `\goodfoot`, `\newtitlepage{title}{author}{date}`, `\newtable{caption}{colspec}{header}{rows}{label}` with `\reftable{label}`, `\boxanswer{equation}`, `\shift{factor}{text}`; strings, a column spec and one number (a doc-kind way as `exam.schooldocs`, a different package) | pdf | - |
| `struct.input` | file inclusion by path: kernel `\input`, `\include` (starts a new page before and after) and `\includeonly`, and the `import` package (CTAN) `\import{dir}{file}` `\subimport` `\includefrom` `\inputfrom`; two string arguments, a directory and a file name (not `pg.standalone-pkg`, whose sub-files carry their own preamble; not `struct.simplesystemtex`, a whole multi-file engine) | pdf | - |
| `inv.zugferd` | `zugferd` (CTAN, TeX Live, LPPL 1.3c; expl3): embeds a Factur-X/XRechnung XML e-invoice in the PDF; `\usepackage[format=...]{zugferd}` (`xrechnung3.0` `xrechnung2.3` `basic` `minimum`; booleans `zugferd` `write-xml` `auto-exemption` `unknown-value-warning`, string `xml-file`), `\SetZUGFeRDData{key=value}` (document-type, id, date, currency, seller, buyer, payment-means, unit and tax keys), `\InsertZUGFeRDData` and the `ZUGFeRD` environment; the per-item and per-sum XML calls come from an invoice package the author writes, so the way holds the data and the attachment, not a visible invoice layout (not `inv.simpleinvoice` or `inv.invoice2`, visible invoices; not `meta.pdfx`) | pdf | - |
| `inv.invoice2` | `invoice2` (CTAN, TeX Live, MiKTeX, GPL 3+): an invoice item table with VAT; `\usepackage[vat=,included-vat=,currency-symbol=,currency-fraction-digits=,currency-in-header,colorize,odd-color=,even-color=,title-color=,total-color=]{invoice2}`, body `invoice` environment (same keys) with `\invoiceitem[VAT]{amount}{name}{price}` and `\invoicesingleitem[VAT]{name}{price}`, `\invoiceoptions{keys}`; sums net, VAT and gross, and drops the amount, VAT and unit-price columns when every row is single and VAT-free; prints only the table and totals, no title, parties or bank line (a sibling of `inv.simpleinvoice` and `inv.facture-belge`; not `tbl.calctab`, `tbl.longtable` or `tbl.siunitx`) | pdf | - |
| `songbook.songs` | `songs` (CTAN, TeX Live, GPL 2; Kevin W. Hamlen): a lyric-and-chord song book; `\usepackage[chorded]{songs}` (output modes `chorded` `lyric` `slide` `trans`), `\songcolumns{n}`, length `\versenumwidth`, body `\songsection{title}`, `songs` environment, `\beginsong{title}[by=,cr=,index=]` ... `\endsong`, `\beginverse`/`\endverse`, `\beginchorus`/`\endchorus`, inline `\[chord]` before a syllable | pdf | - |
| `exam.competences` | `competences` (CTAN, TeX Live, LPPL 1.3): a skill and points tracker for a graded assessment; `\usepackage{competences}`, declarations `\declareprefix{str}` `\declarecompetence{str}`, body `\addcompetence[points]{str}` after each question, `\addGlobalCompetence[points]{str}`, sum-up tables `\tableaupartie{part}` `\tableauprefix{list}` `\tableaucompetences`; values are strings, a comma list and an integer, and the table strings are French and fixed; loads `todonotes`, `datatool`, `etoolbox` and `longtable` (not `exam.questions`, which is question environments) | pdf | - |
| `label.mceinleger` | `mceinleger` (CTAN, TeX Live; needs `rotating`): a music-cassette cover or insert of framed panels with rotated side text; `\usepackage{mceinleger}` and body `\huelle{back}{spine}{front}{pos}` or `\einleger{back}{spine}{front}{pos}{flap}{flap-pos}`; strings and a `\framebox` position list, the sizes fixed in the package (not `label.flabels` or `ticket.sheet`) | pdf | - |
| `recipe.xcookybooky` | `xcookybooky` (CTAN, TeX Live, MiKTeX, LPPL 1.3; v1.5; needs the CTAN `emerald` fonts): a recipe card or recipe collection; `\usepackage{xcookybooky}` and body `recipe[portion, preparationtime, bakingtime, source]{title}` with `\graph{}`, `\ingredients{qty & item \\ ...}`, `\preparation{...}`, `\suggestion[title]{...}`, `\hint{...}` and `\step` | pdf | - |

## Restricted: ways that count as content or artwork, never as template looks

These are published and generic, but their parameters are programs or free
drawings. Used inside a figure or table they are content (`Content-opaque:`).
Used to draw the template's own identity they are `ART`, a blocker.

| id | what it is | engine | Flouest |
|---|---|---|---|
| `art.tikz` | `tikz`/`pgf`/`pgfplots`/`tikz-cd` pictures | pdf | - |
| `art.pstricks` | `pstricks`/`picture` environment | pdf | - |
| `art.content-package` | specialised content packages (chemistry, music, circuits, linguistics; game boards and puzzle grids: `Scrabble` with `EnvScrabble` and `\ScrabblePutWord`, `sudokubundle` with `\sudoku{file}` and `\sudokusolve{file}`) | pdf | - |

## Change log

| Lib | When | What |
|---|---|---|
| v0 | seed | the sections above, from the 21 printers in `JSON->Latex Compiler/src/Packages/`, what General's output loads, and the standard ways for each component. Nothing read from a zip yet. |
| v1 | batch pilot | 35 ways accepted: `class.flashcard`, `class.ulthese`, `class.lebhart`, `class.gsemthesis`, `class.ltxguide`, `class.ltxdoc`, `class.ucsmonograph`, `class.abntex2`, `page.adjustwidth`, `cols.balance`, `pg.emptypage`, `pg.needspace`, `sp.rule`, `sp.manual-space`, `sp.penalties`, `sp.lettrine`, `font.display`, `font.newunicodechar`, `color.transparent`, `lang.projlib`, `meta.documentmetadata`, `front.datetime`, `front.doclicense`, `toc.tocbasic`, `list.enumerate-pkg`, `list.scrextend`, `note.notecolumn`, `math.kernel`, `math.icomma`, `fig.newfloat`, `slide.beamer-section-hook`, `ltr.envlab`, `cv.timeline`, `ticket.sheet`, `legal.contract`. Merged, no line added: `font.opensans` into `font.helvet` (a sans text-face package is the parameter), `bib.abntex2cite` into `bib.apacite` (a standard-specific citation package, like `chicago`/`harvard`/`jurabib`). Duplicate proposals folded into one line: `sp.lettrine`, `math.kernel`. Rejected: none. |
| v2 | batch b01 | 30 ways accepted: `cols.twocolumn-cmd`, `pg.standalone-pkg`, `hf.extramarks`, `sp.frenchspacing`, `sp.selnolig`, `font.nfss`, `lang.bidi`, `lang.translator`, `lang.ptex`, `meta.class-native`, `front.titlepic`, `quote.verse-pkg`, `quote.dialogue`, `mark.nth`, `mark.menukeys`, `fn.footnotebackref`, `note.mparhack`, `math.nicefrac`, `fig.class-native`, `box.stackengine`, `exam.schooldocs`, `exam.rtl-questions`, `label.flabels`, `inv.simpleinvoice`, `notebook.ftc`, `cal.kalender`, `ltr.formlett`, `poster.modernposter`, `poster.tcbposter`, `dtx.doc`. New engine tag `ptex` (for `lang.ptex`). Merged, no line added (the existing line's text widened): `font.symbols` into `font.icons` (a symbol-glyph package is the parameter, as `font.opensans` into `font.helvet`), `lang.polski` into `lang.babel` (a language-specific support package is the parameter, as `bib.abntex2cite` into `bib.apacite`), `tbl.tabularray` into `tbl.nicematrix` (an alternative table package is the parameter, as `tabu` already is); `slide.prosper` into `class.prosper` (a class's own vocabulary is recorded under its class way, whose line the script fills; the dvips toolchain stays an EXTERNAL/class note in the zip). Duplicate proposals folded into one line: `sp.frenchspacing` (two zips), `pg.standalone-pkg` (proposed as `pg.subfile` and `pg.standalone-input`). Renamed on acceptance: `code.doc` to `dtx.doc` (a package that serves one kind of document is a doc-kind way). Rejected: none (`hf.extramarks` kept: `extramarks.sty` ships in the `fancyhdr` distribution, though ctan.org/pkg/extramarks is a 404). |
| v3 | batch b02b03 | 20 ways accepted: `cols.vwcol`, `pg.pgfpages`, `sp.ellipsis`, `font.serif-pkg`, `font.exscale`, `meta.glyphtounicode`, `front.aidisclose`, `front.hep-title`, `mark.contour`, `mark.numspell`, `fig.svg`, `tbl.calctab`, `code.upquote`, `box.eqparbox`, `slide.pdfpc-movie`, `slide.colourchange`, `ltr.envelope-letter`, `logbook.dmlb`, `struct.simplesystemtex`, `inv.facture-belge`. Merged, no line added (the existing line's text widened): `front.datemultical` into `front.datetime` (a date-printing package is the parameter), `math.xfrac` into `math.nicefrac` (another slash-fraction package), `draft.lipsum` into `draft.todo` (a drafting-aid package; the text it prints is filler content), `mark.hologo` into `font.icons` (considered by two analysts, never proposed; a logo-by-name package, as `font.symbols`), `code.pygmentex` into `code.minted` (a second Pygments highlighter with the same EXTERNAL toolchain), `font.garamond` into `font.serif-pkg` (a serif text-face package is the parameter, as `font.opensans` into `font.helvet`; one new line serves it and `sourceserifpro`). Merged into a class way, no component line: `front.unswcover` into `class.unswcover`, `front.navydocs` into `class.navydocs`, `front.osda` into `class.osda`, `thesis.unamthesis` into `class.unamthesis`, `paper.hep-paper` into `class.hep-paper`, `cal.wallcalendar` into `class.wallcalendar`, `exam.class-native` into `class.exam-lite` (a one-institution cover or front-matter package, a thesis style, a house style, a class or a published class's own vocabulary is class-like; the vocabulary is recorded under the class way). `toc.class-native` into `front.class-native` (a mention, not a proposal: the lib's `toc.*` lines sit in the front-matter section). Duplicate proposals folded into one line: `box.eqparbox` (two zips), `fig.svg` (two zips). Rejected: none. |
| v4 | batch b04 | 27 ways accepted: `sp.shapepar`, `sp.truncate`, `pg.enlarge`, `page.pdfscreen`, `meta.accsupp`, `xref.xr`, `xref.hypcap`, `front.uni-titlepage`, `fn.fixfoot`, `math.subdepth`, `math.mleftright`, `fig.epstopdf`, `tbl.arydshln`, `mark.case`, `slide.texpower`, `slide.hackthefootline`, `slide.beamersubframe`, `card.gcard`, `cal.termcal`, `report.practicalreports`, `struct.input`, `inv.zugferd`, `inv.invoice2`, `songbook.songs`, `exam.competences`, `label.mceinleger`, `recipe.xcookybooky`. Merged, no line added (the existing line's text widened; in each case the same type of effect, with the package as the parameter): `lang.xepersian` into `lang.polyglossia` (a language-specific XeLaTeX support package, as `lang.polski` into `lang.babel`), `xref.xr-hyper` into `xref.xr` (the sibling package of the same `\externaldocument`; W1 for `xr-hyper` read at ctan.org/pkg/xr-hyper), `lang.translations` into `lang.translator`, `lang.dirtytalk` into `lang.csquotes`, `idx.idxcmds` into `idx.makeidx`, `bg.wallpaper` into `bg.background`, `sp.dashrule` into `sp.rule`, `sp.nowidow` into `sp.penalties`, `num.dozenal` into `num.counters`, `meta.cmap` into `meta.glyphtounicode`, `font.fix-cm` into `font.exscale`, `bib.breakcites` into `bib.cite-pkg`, `fn.dblfnote` into `fn.footmisc`, `toc.multitoc` into `toc.etoc`, `mark.numprint` into `mark.siunitx`, `color.colordvi` into `color.color`, `dtx.hypdoc` and `dtx.codedescribe` into `dtx.doc`, `slide.beamer-varbox` into `slide.beamer-template` (it is a template name the package supplies to `\setbeamertemplate`; `slide.hackthefootline` kept apart because it has its own commands), `meta.anonymous-acm` into `draft.todo` (a review aid), `exam.esami` and `exam.mcexam` into `exam.questions` (question-bank packages), `list.hang` into `sp.lengths` (W2 is not established for `hang`: ctan.org/pkg/hang names environments only; `\hangindent` and `\hangafter` are the raw parameters), `game.scrabble` and `puzzle.sudokubundle` into `art.content-package` (a game board or puzzle grid is content, held as `Content-opaque:`; the parameters are a word list or a file, as chemistry and music), `mark.textcase` into `mark.case` (the same commands proposed by two zips). Merged into a class way, no component line: `exam.ou-tma` into `class.ou-tma` (a whole-document template for one institution), `fn.class-native` into `class.scrbook` (a mention, not a proposal: `\deffootnote` is KOMA vocabulary). Duplicate proposals folded into one line: `fig.epstopdf` (three zips), `xref.hypcap` (proposed as `xref.hypcap` and `cap.hypcap`), `mark.case` (proposed as `mark.case` and `mark.textcase`). Rejected: `sys.compat-load` (`fixltx2e` and `etex`: load-only packages with no printed effect, so not a component; the zip's verdict does not rest on them), `sp.xspace` (a macro-body helper whose only use is the tail of a zip-local `\newcommand`, which reduces by inline expansion; there is no node content to wrap, so W4 fails), `xref.upref` (passes W1 to W4, but no sample loads it, so recovery does not need it; a zip that loads it may propose it again). |
