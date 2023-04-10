---
title: How a rocket engine works
description: Learn about how rocket engines work!
slug: how-rocket-engines-work
date: 2022-03-18
draft: true
image:
categories:
  - Rocket engines
tags:
  - Physics
  - Thermodynamics
  - Rockets
---

## Disclaimer

This post is based on my "Studieområdeprojekt" (SOP), which is a big academic assignment given to students in technical high schools (HTX) in Denmark, including (the former) me. This is more or less a dump of my assignment, but I plan on splitting it up into more posts to make it more digestible.

## Teori

Der gennemgås først noget teori som er nødvendigt for at forstå videre udledninger.

### Matematik

#### Felter

Et felt i matematikken er en funktion som tilknytter en værdi til alle punkter i et rum. Felter kan være endimensionelle, hvilket bare er en normal funktion, todimensionelle, tredimensionelle, så høj-dimensionelle som det skulle være. Et felt kan udvikle sig i tid, hvilket kan ses som blot en ekstra dimension. Generelt kan et mangedimensionelt felt som udvikler sig i tid skrives således:
$$
\begin{align}
    \phi = \phi(x, y, z, \cdots, t) \nonumber
\end{align}
$$
Hvor $\phi$ er en vilkårlig størrelse. Felter kan være skalarer, vektorer og endda matricer.

#### Infinitessimalregning i felter

Da felter er funktioner med flere variable kan de ikke "bare"\ differentieres. Det skal specificeres hvilken variabel funktionen differentieres i forhold til. De andre variable tænkes så som konstante. Dette hedder en partiel afledt. Feltet $\phi$ afledt i forhold til z-retningen skrives f.eks således:
$$
\begin{align}
    \frac{\partial \phi}{\partial z} \nonumber
\end{align}
$$
Integraler i felter er også lidt anderledes. For integraler endimensionelle felter, altså normale funktioner, er integrationsgrænserne blot 2 tal. I todimensionelle felter kan et dobbeltintegral og kurveintegral defineres. Et dobbeltintegral skrives således:
$$
\begin{align}
    \iint_R \phi \,dA \nonumber
\end{align}
$$
Det kan tænkes at dele et område, $R$, af planet op i infinitessimale små areal-elementer, og summe feltets værdi på hvert punkt ganget med det infintessimale overfladeareal. Det er altså et slags todimensionelt integral, hvor grænsen er områdets "kant". \\\\
Igennem et felt kan en kurve tegnes. Hvert punkt på kurven har en værdi fra feltet, så gås en tur langs kurven kan en graf over feltets værdi som funktion af afstanden langs kurven tegnes. Integralet af denne funktion er et kurveintegral. Starter og slutter kurven samme sted haves et lukket kurveintegral. Åbne og lukkede kurveintegraler over kurven $L$ igennem feltet $\phi$ skrives respektivt:
$$
\begin{align}
    \int_L \phi \,ds \nonumber \\\
    \oint_L \phi \,ds \nonumber
\end{align}
$$
I 3 dimensioner kan ligeledes et lukket og åbent kurveintegral defineres, såvel som et overfladeintegral. Da overflader i 3D kan "bukke", kan et lukket overflade integral også defineres. Et lukket overfladeintegral er integralet over en overflade der omslutter et område af rummet komplet, tænk f.eks overfladen af en bold i modsætning til et papir. Åbne og lukkede overfladeintegraler over overfladen $S$ i et tredimensionelt felt $\phi$ skrives:
$$
\begin{align}
    \iint_S \phi \,dS \nonumber \\\
    \oiint_S \phi \,dS \nonumber
\end{align}
$$
I tre dimensioner kan yderligere defineres et volumenintegral som deler et område af rummet ind i infinitessimale volumen-elementer og summerer feltet gange volumenet af disse. Volumenintegralet over volumenet $V$ i feltet $\phi$ skrives således:
$$
\begin{align}
    \iiint_V \phi \,dV \nonumber
\end{align}
$$
Vektorfelter kan også integreres, ved brug af f.eks prik- og krydsproduktet. Tænkes f.eks et tredimensionelt overfladeintegral har hvert element et overfladeareal $dA$ og en normalvektor $\hat{n}$. Ønskes det at måle hvor meget et vektorfelt "går igennem"\ en overflade, kan prikproduktet mellem vektorfeltet $\vec{v}$ og overfladenormalen ganget med overfladearealet integreres over overfladen:
$$
\begin{align}
    \iint_S \vec{v} \cdot \hat{n} \,dA \nonumber
\end{align}
$$
Ofte kombineres $\hat{n}$ og $dA$ til en vektor $\hat{n} \cdot dA = d\vec{S}$, hvis længde er lig det infintessimale overfladeareal og har samme retning som normalen. Således kan forrige ligning også skrives:
$$
\begin{align}
    \iint_S \vec{v} \cdot \,d\vec{S} \nonumber
\end{align}
$$
Dette bruges senere, f.eks i forbindelse med massebevarelse.

### Termodynamik og gasser

#### Intensive og ekstensive variabler

En cylinder af gas har et bestemt volumen, en bestemt stofmængde og masse. Disse er såkaldte ekstensive egenskaber, som kun et system kan have, og som afhænger af størrelsen af systemet. Det giver ikke mening at spørge hvad massen eller volumenet af et punkt er. Egenskaber som densitet, temperatur og tryk er derimod intensive variabler der godt kan defineres i hvert enkelt punkt. I analysen af flydende gasser og væsker haves sjældent et endeligt volumen, så der kigges sjældent på masse, men i stedet på densitet, altså masse pr. volumen. Der kigges ikke på intern energi, men specifik intern energi, altså intern energi pr. masse. Her er en liste over intensive variabler som vil blive brugt i dette projekt:
\begin{itemize}
    \item Specifik intern energi: $e = \frac{E}{m}$
    \item Specifik entalpi: $h = \frac{H}{m}$
    \item Densitet: $\rho = \frac{m}{V}$
    \item Specifik volumen: $v = \frac{v}{m} = \frac{1}{\rho}$
    \item Specifik varmekapacitet: $c = \frac{C}{m}$
    \item Temperatur: $T$
\end{itemize}
Der er også brug for en version af idealgasloven som ikke indeholder ekstensive variabler som stofmængde og volumen. Den normale gaslov ser sådan ud:
$$
\begin{align}
    p V = n \bar{R} T
\end{align}
$$
Her er $\bar{R}$ den universelle gaskonstant. I fluidmekanik bruges oftest specifikke gaskonstanter i stedet, defineret som
$$
\begin{align}
    R = \frac{\bar{R}}{M} \nonumber \\\
    \bar{R} = R M
\end{align}
$$
Hvor $M$ er molarmassen. Ligning \ref{eq:universalgasconstant} erstattes ind i Ligning \ref{eq:extensiveidealgaslaw}:
$$
\begin{align}
    p V = n R M T \nonumber
\end{align}
$$
Stofmængden og molarmassen kombineres til massen, og der deles med volumen for så at få densitet på højre side:
$$
\begin{align}
    \boxed{p = \rho R T}
\end{align}
$$
Denne form af gasloven relaterer kun intensive variabler til hinanden, og kan derfor bruges på punkter og ikke kun systemer med en endelig størrelse. \\\\
En idealgas' molare varmekapaciteter og gaskonstanten er relateret via følgende relation (\cite[s.150]{orbita}):
$$
\begin{align}
    c_{mp} = c_{mv} + \bar{R} \nonumber
\end{align}
$$
Deles med molarmassen fås de specifkke varmekapaciteter og gaskonstant:
$$
\begin{align}
    \boxed{c_p = c_v + R}
\end{align}
$$

#### Adiabatiske og isentropiske processer

En adiabatisk proces er en termodynamisk proces hvorunder der ikke er sker noget tilførsel af varme. Overførsel af energi kan altås kun foregå ved mekanisk arbejde (\cite[s.153]{orbita}). Sker yderligere ingen andre irreversible processer som diffusion eller intern friktion (viskositet), forbliver entropien konstant. Dette kaldes en isentropisk proces, og følgende relationer kan benyttes til at finde forskellige størrelser under sådan en proces (\cite[s.30]{compflow}):
$$
\begin{align}
    \frac{p_2}{p_1} = \left(\frac{T_2}{T_1}\right)^{\frac{\gamma}{\gamma - 1}} \\\
    \frac{\rho_2}{\rho_1} = \left(\frac{T_2}{T_1}\right)^{\frac{1}{\gamma - 1}} \\\
    \frac{p_2}{p_1} = \left(\frac{\rho_2}{\rho_1}\right)^\gamma
\end{align}
$$
$\gamma$ (gamma) er det såkaldte \emph{varmefyldeforhold}, eller \emph{adiabatkonstant}, defineret som
$$
\begin{align}
    \gamma = \frac{c_p}{c_v}
\end{align}
$$
Kendes en gas' $\gamma$, $R$ og temperatur, kan lydens hastighed i gassen, $a$, beregnes således (\cite[s.77]{compflow}):
$$
\begin{align}
    a = \sqrt{\gamma R T}
\end{align}
$$
Machtallet er forholdet mellem hastigheden af noget (gassen selv, eller et objekt i gassen), og den lokale lydhastighed:
$$
\begin{align}
    M = \frac{u}{a} = \frac{u}{\sqrt{\gamma R T}}
\end{align}
$$

### Fluider

Ordet fluid (fra engelsk "fluid") dækker over alt som kan flyde som et kontinuum som f.eks gasser (inklusiv plasma) og væsker. Fluider kan modelleres som en samling af felter der fylder rummet og udvikler sig i tid. Der er et felt for temperatur, for tryk, for densitet, specifik energi, hastighed, etc. Samlet kaldes felterne for strømningsfeltet (se stikordsregister med engelske ækvivalenter i bilag \ref{app:stikord}). Nogle af disse felter, som f.eks tryk, densitet og temperatur er skalarfelter, mens hastighed er et vektorfelt. Disse felter kan udvikle sig i tid: vinden kan ændre retning, det kan blive varmere og koldere, trykket kan ændre sig, etc. Felterne for hastighed og temperatur kan f.eks skrives således:
$$
\begin{align}
    \Vec{v} = \Vec{v}(x, y, z, t) \nonumber \\\
    T = T(x, y, z, t) \nonumber
\end{align}
$$
Fluidmekanikken beskriver hvordan fluider bevæger sig, ved f.eks at beskrive hvordan disse felter opfører sig. Derved kan engienører og videnskabsfolk forudsige hvordan fluider interagerer med f.eks fly, raketter og både, og hvordan de opfører sig inde i dampturbiner, raketmotorer og jetmotorer.

#### Forskellige perspektiver

I strømningsfelterne kan et abstrakt volumen forestilles, dette kaldes et kontrolvolumen. Det kan være et fast område af rummet som ikke flytter sig, hvorigennem fluiden strømmer, eller det kan være et volumen som flyder med strømmen, hvor overfladen følger hastighedsfeltet sådan at det hele tiden indeholder den samme fluid. Ligninger for bevarelse af forskellige fysiske størrelser kan så laves ved at beskrive på hvordan disse "flyder"\ ind og ud af et kontrolvolumen og ophober sig inde i det, ved brug af diverse overflade- og volumenintegraler. \\
Felterne kan også beskrives ved at forestille at kontrolvumenerne bliver uendeligt små omkring et punkt. På den måde tager ligningerne form af vektor differentialligninger. Et eksempel er Navier-Stokes ligning som beskriver impulsbevarelse. Denne form af ligningerne er dog ikke relevant for dette projekt.

---

## Generel konstant kvasi-1D strømning

Mange strømningsproblemer involverer fluider der løber internt i rør med varierende tværsnitsarealer. Laves nogle antagelser kan det siges at alle strømningsvariablerne udelukkende er funktioner af afstanden langs røret. Densiteten, hastigheden, temperaturen, trykket, osv. er altså konstante over et tværsnit af røret. Denne tilnærmelse passer nogenlunde for strømme ved lav viskositet igennem f.eks rør, vindtuneller, raketmotorer og jetmotorer, hvor kan ses bort fra friktion med væggen. Da egenskaberne kun varierer i en dimension, men tværsnitsarealet også kan variere, kaldes dette en kvasi-endimensionel strøm.\\\\
I følgende underafsnit udledes to modeller for konstant kvasi-1D strømning. Konstant betyder at strømningsfeltet ikke ændrer sig med tid, altså at der er gået nok tid til at en ligevægt har indstillet sig. Først benyttes generelle bevarelsesligninger på et generelt kvasi-1D kontrolvolumen og resultaterne fra dette bruges så til at udlede relationer for diverse størrelser i først en ikke-kompressibel og derefter en kompressibel strøm.

### Konstant kvasi-1D massebevarelse

\begin{figure}[h!]
    \centering
    \includegraphics[width=0.8\textwidth]{Q1DCV.pdf}
    \caption{Et kontrolvolumen som repræsenterer en kvasi-endimensionel strøm.}
\end{figure}
I dette underafsnit udledes ligningen for massebevarelse. Der startes med den generelle ligning for massebevarelse i en tredimensionel strøm (denne kommer fra (\cite[s.46]{compflow}). se Bilag \ref{app:massconsderiv} for en løs udledning af den):
$$
\begin{align}
    \frac{\partial}{\partial t} \iiint_V \rho \,dV = - \oiint_S \rho \vec{v} \cdot d\vec{S} \nonumber
\end{align}
$$
Ligningen beskriver et kontrolvolumen der er fast i rummet. Volumenintegralet på venstre side beskriver massen inde i kontrolvolumenet ved at integrere densiteten over det. Den tidsafledte af dette er hvor hurtigt masse opbygger sig inde i volumenet. Det lukkede overfladeintegral på højre side beskriver massefluxen over volumenets grænse, ved at integrere masse-udstrømningen over hele grænsen. Hastigheden prikket med "areal-normal-vektoren"\ giver volumenstrømmen, ganget med densitet giver massestrømmen. Ligningen siger altså at hvor hurtigt masse ophober sig i et område af rummet, er lig netto-indstrømningen af masse til området og intet andet. Masse kan altså ikke bare opstå. Denne ligning bruges på kontrolvolumenet i Figur \ref{fig:Q1DCV}. Overfladeintegralet på højre side af ligningen kan brydes op i 3 integraler, et for hver overflade:
$$
\begin{align}
    \oiint_S \rho \vec{v} \cdot d\vec{S} = \iint_1 \rho \vec{v} \cdot d\vec{S} + \iint_2 \rho \vec{v} \cdot d\vec{S} \nonumber
\end{align}
$$
Da der ikke kan løbe fluid igennem overflade 3 bliver prikproduktet mellem hastigheden og normalen 0. Det bidrager altså ikke, og er derfor udeladt. \\
Da strømmen er konstant er alle tidsafledte lig 0, og venstre side af massebevarelsesligningen sættes til 0. Derved fås følgende:
$$
\begin{align}
    \iint_1 \rho \vec{v} \cdot \hat{n} \,dA + \iint_2 \rho \vec{v} \cdot \hat{n} \,dA = 0 \nonumber
\end{align}
$$
$d\vec{S}$'erne er blevet brudt ned til normalvektoren og overfladearealet for forståelsens skyld. Da strømningsvariablerne kun er funktioner af x, og overflade 1 og 2 står lodret på denne og er helt flade, varierer hverken tryk, hastighed eller overfladenormal igennem integralet, og disse kan derfor flyttes ud foran.
$$
\begin{align}
    \rho_1 \vec{v} \cdot \hat{n}_1 \iint_1 dA + \rho_2 \vec{v} \cdot \hat{n}_2 \iint_2 dA = 0 \nonumber
\end{align}
$$
Integralerne bliver nu blot til arealerne af de respektive overflader. Overfladenormalerne og hastigheden peger begge udelukkende langs x-aksen, så deres prikprodukt reduceres til produktet af vektorernes respektive x-komposanter. De to overfladenormaler peger dog i hver deres retning. For overflade 1 er normalens x-komposant $-1$, mens overflade 2's er $1$. Ved at indsætte dette og flytte ledet for overflade 2 over på den anden side af ligningen fås endeligt:
$$
\begin{align}
    \boxed{\rho_1 u_1 A_1 = \rho_2 u_2 A_2 = \dot{m}}
\end{align}
$$
Hastigheden er blevet skrevet som blot sin x-komposant $u$. Produktet af densitet, hastighed og tværsnitsareal er massestrømmen $\dot{m}$, så ligningen siger at massestrømmen ind og ud af kontrolvolumenet er den samme. Der bygges altså ikke masse op inde i det. Da kontrolvolumenet er valgt vilkårligt, kan overflade 1 og 2 placeres vilkårlige steder i en kvasi-endimensionel strømning. Kontrolvolumenet behøver ikke engang at være lige, så længe at der ikke løber fluid ud fra siden (overflade 3).

### Konstant adiabatisk kvasi-1D energibevarelse

I dette underafsnit udledes en ligning for energibevarelse. Igen startes med den generelle ligning i 3D (fra (\cite[s.53]{compflow}), løs udledning i Bilag \ref{app:nrgconsderiv}):
$$
\begin{align}
  \overbrace{\frac{d}{dt} \iiint_V \rho \left(e + \frac{v^2}{2}\right) dV}^\text{A} = \overbrace{\iiint_V \dot{q} \rho dV}^\text{B} + \overbrace{\iiint_V \rho \vec{f} \cdot \vec{v} dV}^\text{C}  - \overbrace{\oiint_S p \vec{v} \cdot d\vec{S}}^\text{D} - \overbrace{\oiint_S \left(e + \frac{v^2}{2}\right) \rho \vec{v} \cdot d\vec{S}}^\text{E} \nonumber
\end{align}
$$

A beskriver raten af ophobning af intern og kinetisk energi inde i kontrolvolumenet. $e$ er den specifikke interne energi, og $\frac{v^2}{2}$ er den specifikke kinetiske energi. Det ganges så med densitet for at få en enhed pr. volumen i stedet for masse, og dette integreres så over hele volumenet for at få den samlede kinetiske og interne energi.

B beskriver varmen "genereret"\ inde i volumenet, f.eks pga. absorbtion af stråling. Variablen $\dot{q}$ er en effekt pr. masse. Igen ganges med densitet for at få det pr. volumen, og det integreres så over hele volumenet.

C beskriver effekten af arbejdet fra volumenkræfter på væsken inde i volumenet. $\vec{f}$ er kraften pr. masse (acceleration). Dette prikkes med hastigheden for at få en effekt pr. masse, dette ganges så med densitet og integreres.

D beskriver den effekt der løber ud af kontrolvolumenet pga. dettes arbejde på omgivelserne. Som sagt er effekt lig kraft prikket med hastighed. Størrelsen af kraften på et overfladeelement af kontrolvolumenet er lig trykket gange overfladearealet. Ganges dette på normalvektoren fås den kraft som trykket indeni påvirker overfladen med. Dette prikkes med hastigheden for at få effekten af volumenets arbejde på væsken der flyder gennem overfladen. Væske der flyder ind vil udføre arbejde på volumenet, og væske der flyder ud vil blive arbejdet på. Da ledet beskriver effekten \emph{tilført} omgivelserne fra kontrolvolumenets arbejde, trækkes ledet fra.

E beskriver netto-effekten af intern og kinetisk energi som massestrømmen tager med sig \emph{ud} gennem overfladen. Derfor trækkes dette også fra.
\end{enumerate}

Ligningen benyttes på kontrolvolumenet i Figur \ref{fig:Q1DCV}. \\
Igen er strømningen konstant, så alle tidsafledte fjernes. Det antages desuden at $\dot{q} = 0$, altså en adiabatisk proces, og at der ikke er nogen volumenkræfter som f.eks tyngdekraft, altså $\vec{f} = 0$. Integralerne der indeholder disse to variable kan derfor også fjernes. Tilbage er følgende:
$$
\begin{align}
    \oiint_S \left(e + \frac{v^2}{2}\right) \rho \vec{v} \cdot d\vec{S} = - \oiint_S p \vec{v} \cdot d\vec{S} \nonumber
\end{align}
$$
Det kan ses at netto-effekten af intern og kinetisk energi som løber ud gennem overfladen er lig effekten fra volumenets arbejde på fluiden. Ligesom med massebevarelse deles hver af integralerne op i 3, et for hver overflade. Integralerne for overflade 3 kan ligeledes fjernes:
$$
\begin{align}
    \iint_1 \left(e + \frac{v^2}{2}\right) \rho \vec{v} \cdot d\vec{S} + \iint_2 \left(e + \frac{v^2}{2}\right) \rho \vec{v} \cdot d\vec{S} = - \iint_1 p \vec{v} \cdot d\vec{S} - \iint_2 p \vec{v} \cdot d\vec{S} \nonumber
\end{align}
$$
Variablerne antages at være konstante på tværs af alle overfladerne, så de trækkes udenfor, og integralerne erstattes med arealer:
$$
\begin{align}
    \left(e_1 + \frac{v_1^2}{2}\right) \rho_1 A_1 \vec{v}_1 \cdot \hat{n}_1 + \left(e_2 + \frac{v_2^2}{2}\right) \rho_2 A_2 \vec{v}_2 \cdot \hat{n}_2 = - p_1 A_1 \vec{v}_1 \cdot \hat{n}_1 - p_2 A_2 \vec{v}_2 \cdot \hat{n}_2 \nonumber
\end{align}
$$
Ligesom før simplificeres prikprodukterne:
$$
\begin{align}
    - \left(e_1 + \frac{u_1^2}{2}\right) \rho_1 A_1 u_1 + \left(e_2 + \frac{u_2^2}{2}\right) \rho_2 A_2 u_2 = p_1 A_1 u_1 - p_2 A_2 u_2 \nonumber
\end{align}
$$
Til sidst grupperes de led der har med den samme overflade at gøre på hver sin side:
$$
\begin{align}
    \boxed{\left(e_1 + \frac{u_1^2}{2}\right) \rho_1 A_1 u_1 + p_1 A_1 u_1 = \left(e_2 + \frac{u_2^2}{2}\right) \rho_2 A_2 u_2 + p_2 A_2 u_2}
\end{align}
$$
Dette er den generelle energibevarelsesligning for kvasi-1D, konstant, adiabatisk strømning. \\\\
Med de generelle ligninger for kvasi-1D energibevarelse og massebevarelse kan der nu opstilles to modeller: en for en inkompressibel strømning hvor densiteten er konstant (væske) og en model for kompressibel strømning, hvor den ikke er (gas).

---

## Inkompressibel strømning

Nu hvor energi- og massebevarelsesligningerne er udledt, kan en model for inkompressibelt flow igennem et rør opstilles. I denne udledning antages at fluidens densitet forbliver konstant i både tid og rum:
$$
\begin{align}
    \rho_1(x, y, z, t) = \rho_2(x, y, z, t) = \rho \nonumber
\end{align}
$$
Dette er en meget god tilnærmelse for væsker, og som det skal ses passer det også nogenlunde for gasser ved lavere hastigheder. Sættes dette ind i massebevarelsesligningen fås:
$$
\begin{align}
    \rho u_1 A_1 = \rho u_2 A_2 \Rightarrow \nonumber \\\
    \boxed{u_1 A_1 = u_2 A_2 = \dot{V}}
\end{align}
$$
Farten gange tværsnitsarealet er volumenstrømningen $\dot{V}$, denne er altså konstant igennem et inkompressibelt flow. Dette resultat kan bruges på energibevarelsesligningen (Lignign \ref{eq:EQ1DAdia}), da der er et $A \cdot u$ term i hvert led som kan fjernes. Desuden kan kan densiteterne også sættes lig hinanden:
$$
\begin{align}
    \left(e_1 + \frac{u_1^2}{2}\right) \rho + p_1 = \left(e_2 + \frac{u_2^2}{2}\right) \rho + p_2 \nonumber
\end{align}
$$
Der deles så med densitet for at få følgende:
$$
\begin{align}
    e_1 + \frac{u_1^2}{2} + \frac{p_1}{\rho} = e_2 + \frac{u_2^2}{2} + \frac{p_2}{\rho} \nonumber
\end{align}
$$
For at simplificere yderligere tages et lille sidespor til termodynamikken. \\\\
Den første lov siger at ændringen i intern energi af et system er arbejdet udført på systemet, plus varmen tilført:
$$
\begin{align}
    \Delta e = w + q \nonumber
\end{align}
$$
Da processen er adiabatisk tilføres ikke varme, altså $q = 0$. Da fluidens densitet er konstant kan dens volumen ikke ændre sig, og der kan ikke udføres arbejde på den. Forestilles at systemet er en kube i det frie rum (som på en eller anden måde hænger sammen når der røres ved den), kan systemet godt gives en samlet kinetisk energi ved at skubbe på det, men selve partiklerne inde i har ikke ændret energi i forhold til hinanden. Den interne energi er derfor uændret:
$$
\begin{align}
    \Delta e = 0 \nonumber
\end{align}
$$
Det leder til at de to interne energier i ligningen er ens (og som konsekvens at temperaturen også er konstant), og kan trækkes fra på hver side. Tilbage er ligningen for energibevarelse i en inkompressibel, adiabatisk, kvasi-endimensionel strømning:
$$
\begin{align}
    \boxed{p_1 + \rho \frac{u_1^2}{2} = p_2 + \rho \frac{u_2^2}{2}}
\end{align}
$$
Denne ligning er også kendt som Bernoullis ligning. Ofte inkluderes også et potential-term, der afhænger af højde, men det er ikke relevant for dette projekt. Ligningen siger, at når en væske flyder imellem to punkter, vil trykket falde hvis hastigheden stiger og stige hvis hastigheden falder. Hvorfor hastigheden skulle stige eller trykket falde siger den dog ikke noget om.

### Inkompressibelt hviletryk

En bekvæmt teoretisk referencestørrelse er hviletrykket. Dette er det tryk som en fluid i bevægelse vil opnå, hvis den blev bremset til at stå stille. Det er også kendt som totaltrykket og er angivet ved $p_0$. Forestilles en væske ved tryk $p_1 = p$ og fart $u_1 = u$ som bremses, kan hviletrykket $p_2 = p_0$ findes ved at sætte $u_2$ i Ligning \ref{eq:bernoulli} til 0:
$$
\begin{align}
    p_0 = p + \rho \frac{u^2}{2}
\end{align}
$$
Fysisk set giver det ikke meget mening at have en væske der på et punkt i et rør har en hastighed, og på det andet står stille, da væsken så nødvendigvis må komprimeres, hvilket ifølge antagelserne er umuligt. Det kan forestilles at hviletrykket er det tryk som væsken vil opnå hvis tværsnitsarealet går mod uendeligt. Det smarte ved hviletrykket er at det er konstant igennem en strøm, da $p + \rho \frac{u^2}{2}$ som bekendt ved Ligning \ref{eq:bernoulli} er konstant. Når det først er kendt kan det bruges til at relatere trykket og hastigheden alle andre steder i strømmen, gennem Ligning \ref{eq:incompstagpres}.

### Inkompressibel areal-relation

Det ønskes at finde ud af hvordan en inkompressibel strøm reagerer på ændringer i tværsnitsareal. \\
Først isoleres farten i Ligning \ref{eq:incompstagpres}:
$$
\begin{align}
    u = \sqrt{2 \frac{p_0 - p}{\rho}}
\end{align}
$$
Når trykket $p$ falder eller $p_0$ stiger, vil hastigheden stige. I teorien er der ingen grænse for dette. Lad os nu se hvad sammenhængen mellem tryk og volumenstrøm er.
Ligning \ref{eq:incomppressurespeed} indsættes i Ligning \ref{eq:volflowcons} (massebevarelse):
$$
\begin{align}
    \dot{V} = A \sqrt{2 \frac{p_0 - p}{\rho}}
\end{align}
$$
\begin{figure}[ht]
    \centering
    \includegraphics[width=0.8\textwidth]{Areavoldot.png}
    \caption{Volumenstrøm plottet mod trykforskel $\rho_0 - \rho$ i Ligning \ref{eq:incompvolpresrel}.}
\end{figure}
Volumenstrømmen kan findes med Ligning \ref{eq:incompvolpresrel} hvis tværsnitsarealet, hviletrykket og trykket på et punkt i strømmen kendes, f.eks ved en åbning ud til atmosfæren. Sammenhængen mellem trykforskellen og volumenflow er plottet på Figur \ref{fig:incomppresvolfig}. Når dette er kendt, kan Ligning \ref{eq:volflowcons} bruges til at finde hastigheden andre steder i strømmen, da tværsnitsarealet sandsynligvis er kendt. Ved at isolere $p$ i Ligning \ref{eq:incompvolpresrel} kan trykket også findes alle andre steder i strømmen:
$$
\begin{align}
    p = p_0 - \rho \frac{\dot{V}^2}{2 A^2}
\end{align}
$$
På Figur \ref{fig:incompareapresfig} er trykket plottet som funktion af tværsnitsareal. Selvom det kunne tros at tværsnitsarealet kunne formindskes så meget som ønsket for at få højere hastighed, er dette ikke tilfældet i den virkelige verden. For det første når væsken på et tidspunkt sit damptryk og bliver til gas. For det andet vil friktion med væggen spille en større og større rolle som hastigheden stiger og tværnitsarealet falder, så antagelserne vil passe dårligere og dårligere.
\begin{figure}[ht]
    \centering
    \includegraphics[width=0.8\textwidth]{Pressurearea incomp.png}
    \caption{Tryk plottet mod areal i Ligning \ref{eq:incomppresarea}.}
\end{figure}

---

## Kompressibel strømning

Nu kigges i stedet på en gas, hvor densiteten godt kan ændre sig. Denne udledning er baseret på (\cite{compflow}), men hvor denne bog straks går over til at bruge Machtallet som "reference", holder dette projekt sig til farten eller trykforholdet. Dette gøres for at holde udledningen så relevant for problemstillingen som muligt, og for senere at motivere hvorfor Machtallet normalt bruges. (Hvad "trykforholdet"\ er, ses senere). \\\\
Der startes med ligningen for energibevarelse i en kvasi-1D strømning, Ligning \ref{eq:EQ1DAdia}, gentaget her for bekvemmelighed:
$$
\begin{align}
    \left(e_1 + \frac{u_1^2}{2}\right) \rho_1 A_1 u_1 + p_1 A_1 u_1 = \left(e_2 + \frac{u_2^2}{2}\right) \rho_2 A_2 u_2 + p_2 A_2 u_2 \nonumber
\end{align}
$$
Alle $\rho u A$ termerne er lig hinanden, pr. massebevarelse, men to af ledene mangler et $\rho$. Lad os alligevel se hvad der sker hvis der divideres med $\rho u A$:
$$
\begin{align}
    e_1 + \frac{u_1^2}{2} + \frac{p_1}{\rho_1} = e_2 + \frac{u_2^2}{2} + \frac{p_2}{\rho_2} \nonumber
\end{align}
$$
$\rho$ er densiteten, altså masse pr. volumen. Den omvendte af dette er den specifikke volumen, som er volumen pr. masse:
$$
\begin{align}
    \frac{1}{\rho} = v \nonumber
\end{align}
$$
Erstattes dette ind fås:
$$
\begin{align}
    e_1 + \frac{u_1^2}{2} + p_1 v_1 = e_2 + \frac{u_2^2}{2} + p_2 v_2 \nonumber
\end{align}
$$
Summen af $e$ og $pv$ er definitionen på entalpi:
$$
\begin{align}
    h = e + pv \nonumber
\end{align}
$$
Så disse led kan erstattes:
$$
\begin{align}
    \boxed{h_1 + \frac{u_1^2}{2} = h_2 + \frac{u_2^2}{2}}
\end{align}
$$
Dette er ligningen for energibevarelse i en adiabatisk gasstrøm. Det kan ses at energien kan eksistere enten som entalpi eller kinetisk energi. En stigning i den ene vil altså medføre et fald i den anden. \\
I en ideel gas er entalpien proportionel med temperaturen:
$$
\begin{align}
    h = c_p T \nonumber
\end{align}
$$
Dette erstattes ind:
$$
\begin{align}
    c_p T_1 + \frac{u_1^2}{2} = c_p T_2 + \frac{u_2^2}{2} \Rightarrow \nonumber \\\
    \boxed{T_1 + \frac{u_1^2}{2 c_p} = T_2 + \frac{u_2^2}{2 c_p}}
\end{align}
$$
Denne form af energibevarelsesligningen er brugbar, da temperaturen kan relateres til andre variabler via de isentropiske relationer. Det kan også ses her, at temperaturen i en gasstrøm, i modsætning til væske, \emph{godt} kan ændre sig.

### Kompressible hvilerelationer

Ligesom med hviletrykket i en inkompressibel adiabatisk strømning kan en hviletemperatur findes i en kompressibel adiabatisk strøm ved at sætte $u_2 = 0$ i Ligning \ref{eq:comptempspeed}:
$$
\begin{align}
    \boxed{T_0 = T + \frac{u^2}{2 c_p}}
\end{align}
$$
Denne ligning gælder for en adiabatisk gasstrøm. Antages det yderligere at strømmen også er isentropisk, altså at der ikke sker diffusion, friktion, etc. gælder de isentropiske relationer (Ligning \ref{eq:isentropicprestemp} og \ref{eq:isentropicdenstemp}).
Ligning \ref{eq:stagtempspeed} omskrives lidt for at kunne passes ind i disse to:
$$
\begin{align}
    \frac{T_0}{T} = 1 + \frac{u^2}{2 c_p T}
\end{align}
$$
Dette erstattes ind i de isentropiske relationer:
$$
\begin{align}
    \frac{p_0}{p} = \left(1 + \frac{u^2}{2 c_p T}\right)^{\frac{\gamma}{\gamma - 1}} \\\
    \frac{\rho_0}{\rho} = \left(1 + \frac{u^2}{2 c_p T}\right)^{\frac{1}{\gamma - 1}}
\end{align}
$$
Ledene inde i parenteserne indeholder $T$, som refererer til den lokale temperatur. Denne afhænger af hviletemperaturen og hastigheden og kan erstattes ved hjælp af Ligning \ref{eq:stagtempspeed}:
$$
\begin{align}
    1 + \frac{u^2}{2 c_p T} = 1 + \frac{u^2}{2 c_p \left(T_0 - \frac{u^2}{2 c_p}\right)} \Rightarrow \nonumber \\\
    1 + \frac{u^2}{2 c_p T} = 1 + \frac{u^2}{2 c_p T_0 - u^2} \Rightarrow \nonumber \\\
    1 + \frac{u^2}{2 c_p T} = \left(\frac{2 c_p T_0 - u^2}{2 c_p T_0}\right)^{-1} \Rightarrow \nonumber \\\
    1 + \frac{u^2}{2 c_p T} = \left(1 - \frac{u^2}{2 c_p T_0}\right)^{-1} \nonumber
\end{align}
$$
Erstattes dette tilbage ind i Ligning \ref{eq:presspeedtemp} og \ref{eq:densspeedtemp} og simplificeres fås:
$$
\begin{align}
    \boxed{\frac{p_0}{p} = \left(1 - \frac{u^2}{2 c_p T_0}\right)^{\frac{\gamma}{1 - \gamma}}} \\\
    \boxed{\frac{\rho_0}{\rho} = \left(1 - \frac{u^2}{2 c_p T_0}\right)^{\frac{1}{1 - \gamma}}}
\end{align}
$$
Med disse ligninger kan forholdet mellem hviletemperatur, -tryk og -densitet findes hvis temperaturen og farten kendes et sted i strømmen.
Det kan ses at densiteten ikke ændres betydeligt ved lave hastighed ved at vende Ligning \ref{eq:stagstatdens} på hovedet, og indsætte værdier for luft og en hviletemperatur på $293.15K$.
$$
\begin{align}
    \frac{\rho}{\rho_0} = \left(1 - \frac{u^2}{2 c_p T_0}\right)^{\frac{1}{\gamma - 1}}
\end{align}
$$
Det giver grafen på Figur \ref{fig:densityspeed}.
\begin{figure}[h]
    \centering
    \includegraphics[width=\textwidth]{Densitet.png}
    \caption{$\frac{\rho}{\rho_0}$ plottet i forhold til $u$ i Ligning \ref{eq:densityspeedrecip}. Lavet med desmos.com.}
\end{figure}
Hastigheden skal op på $150 \frac{m}{s}$, hvad der svarer til $540 \frac{km}{h}$, før densiteten falder til bare $90\%$ af hviledensiteten. For lave hastigheder kan det altså antages at densiteten er så godt som konstant, og gassen derfor er inkompressibel. På grafen kan det også ses at der er en maksimal hastighed. Dette er hvor brøken inde i parenteserne er lig 1. Brøken er forholdet mellem den kinetiske energi og hvileentalpien, så den maksimale hastighed er altså der hvor al energien er blevet til kinetisk energi, og temperaturen derfor er $0$K.

### Kompressibel areal-relation

Lad os se hvilken effekt varierende tværsnitsareal har på en kompressibel strømning. Her er det f.eks interessant at kigge på sammenhængen mellem tryk og tværsnitsareal. Der startes med massebevarelse, hvor arealet isoleres:
$$
\begin{align}
    A = \frac{\dot{m}}{u \rho}
\end{align}
$$
$\rho$ kan erstattes ved hjælp af de isentropiske relationer. I Ligning \ref{eq:isentropicpresdens} sættes $[]_1 = []_0$ og $[]_2 = []$, og $\rho$ isoleres:
$$
\begin{align}
    \rho = \rho_0 \left(\frac{p_0}{p}\right)^{-\frac{1}{\gamma}}
\end{align}
$$
Farten og trykket er relaterede via Ligning \ref{eq:stagstatpres}. Farten isoleres i denne:
$$
\begin{align}
    u = \sqrt{2 c_p T_0\left(1 - \left(\frac{p_0}{p}\right)^\frac{1 - \gamma}{\gamma}\right)}
\end{align}
$$
Ligning \ref{eq:pressurespeed} og \ref{eq:densitypressure} erstattes ind i Ligning \ref{eq:compareabase}:
$$
\begin{align}
    \boxed{A = \frac{\dot{m}}{\rho_0} \left(\frac{p_0}{p}\right)^{\frac{1}{\gamma}} \left(2 c_p T_0\left(1 - \left(\frac{p_0}{p}\right)^\frac{1 - \gamma}{\gamma}\right)\right)^{-\frac{1}{2}}}
\end{align}
$$
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Areapressure.png}
    \caption{Areal plottet mod trykforholdet i Ligning \ref{eq:areapresrel}.}
\end{figure}
På Figur \ref{fig:comppresareagraph} er arealet i denne ligning plottet som funktion af trykforholdet $\frac{\rho_0}{\rho}$ (dette kaldes blot "trykforholdet"\ i resten af projektet). En strømning der befinder sig på "venstre side"\ af kurven har et relativt højt tryk, og stort tværsnitsareal. Bliver arealet længere nede ad strømmen lavere, vil trykket også blive lavere (trykforholdet bliver større). Når strømningens mindste tværsnitsareal er nået skal tværsnitsarealet i stedet forstøres for at trykket kan fortsætte med at falde. Da et lavere tryk betyder en større hastighed (pr. Ligning \ref{eq:pressurespeed}) betyder det også at tværsnitsarealet skal forstøres hvis gassen skal komme over en vis fart. Dette er forskelligt fra væskestrømninger, hvor yderligere indsnævring (inden for antagelsernes grænser) altid vil lede til forhøjet fart. Det er også hvorfor raketdyser er formet som de er. Ved dysens minimumsareal bevæger udstødningsgassen sig med en vis hastighed, for at nå en højere udstødningshastighed, og derved kraft, skal tværsnitsarealet udvides. \\\\
Hvad dette minimumsarealet er, sættes af massestrømmen, hviledensiteten og hviletemperaturen. Kigges på det omvendt kan det også siges at massestrømmen sættes af hvileforholdene og strømningens mindste tværsnitsareal, så længe at trykforholdet ved minimumsarealet kan nå langt nok op. Når trykket i minimumsarealet når det kritiske forhold kaldes strømningen "kvalt"\ (oversat fra engelsk - "choked flow"). \\\\
Eksempelvis forestilles et rør mellem to uendelig store lufttanke ved konstante tryk. Røret har en indsnævring på midten. Til at starte med er trykket i begge tanke ens, og der løber ingen gas. Sænkes trykket i den ene tank, begynder der at løbe en gasstrøm. Hviletrykket og hviledensiteten er lig værdierne i tanken ved højere tryk. Antages det at trykket ved rørets udstødning er lig trykket i tanken ved lavt tryk, kan massestrømmen bestemmes ved at isolere $\dot{m}$ i Ligning \ref{eq:areapresrel}:
$$
\begin{align}
    \boxed{\dot{m} = A \rho_0 \left(\frac{p_0}{p}\right)^{-\frac{1}{\gamma}} \sqrt{2 c_p T_0\left(1 - \left(\frac{p_0}{p}\right)^\frac{1 - \gamma}{\gamma}\right)}}
\end{align}
$$
I denne kan udstødningens areal og tryk så indsættes. På Figur \ref{fig:massflowexhaustpressure} er massestrømmen plottet som funktion af trykforholdet ved udstødningen.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Massflow-pressure.png}
    \caption{Massestrøm plottet som funktion af trykforhold ved udstødning i Ligning \ref{eq:massflowexhaust}.}
\end{figure}
Som det kan ses stiger massestrømmen indtil trykforholdet når en kritisk værdi. Det er den samme værdi som på Figur \ref{fig:comppresareagraph}. Som konkluderet tidligere kræver det at tværsnitsarealet udvides fra minimumsværdien for at nå tryk der er lavere end det kritiske tryk. Den eneste måde hvorpå disse tryk ville kunne opnås ved udstødningen er derfor at udstødningsarealet er større end minimumsarealet. Da trykket ved minimumsarealet altid vil være den samme værdi (afhængig af $\gamma$ som vises om lidt, og så længe massestrømmen er høj nok), vil densiteten og hastigheden her også altid have den samme værdi. Derved er massestrømmen nu ikke længere bestemt af udstødningsforholdene, men udelukkende hvile-værdierne og minimumsarealet. \\\\
Hvad er dette kritiske trykforhold? Det kan findes ved at differentiere Ligning \ref{eq:areapresrel} i forhold til trykforholdet, sætte dette til 0 og isolere trykforholdet. Den fulde udledning er i Bilag \ref{app:criticalpressureratio}, men følgende er resultatet:
$$
\begin{align}
    \frac{p_0}{p} = \left(\frac{2}{\gamma + 1}\right)^\frac{\gamma}{1 - \gamma}
\end{align}
$$
Trykforholdet er kun en funktion af $\gamma$, som afhænger af hvilken gas der er tale om. Hvilken fart der opnås ved dette trykforhold kan findes ved at indsætte i Ligning \ref{eq:presspeedtemp} og isolere farten:
$$
\begin{align}
    u^2 = c_p T (\gamma - 1)
\end{align}
$$
Ved hjælp af Mayers relation (Ligning \ref{eq:mayers}) og definitionen på $\gamma$ kan dette reduceres yderligere til:
$$
\begin{align}
    u = \sqrt{\gamma R T} \nonumber
\end{align}
$$
Dette er definitionen på lydhastigheden (Ligning \ref{eq:speedofsound})! $T$ repræsenterer temperaturen ved det kritiske trykforhold, så det er den lokale lydhastighed ved minimumsarealet der måles. Fra definitionen på Machtallet haves (Ligning \ref{eq:machnumber}):
$$
\begin{align}
    M = \frac{u}{\sqrt{\gamma R T}} \nonumber
\end{align}
$$
I dette tilfælde er hastigheden lig lydhastigheden, så ved minimumsarealet bevæger gassen sig med Mach 1!
$$
\begin{align}
    M = \frac{\sqrt{\gamma R T}}{\sqrt{\gamma R T}} = 1 \nonumber
\end{align}
$$
Bemærk at Machtallet kun er en funktion af farten, temperaturen og nogle konstanter. Noget andet som kun er en funktion af farten, temperaturen og nogle konstanter er temperaturforholdet, trykforholdet og densitetsforholdet i Ligning \ref{eq:stagstattemp}, \ref{eq:presspeedtemp} og \ref{eq:densspeedtemp}. Derfor skrives disse ofte som funktioner af Machtallet i stedet. Hvordan disse omskrives gennemgås ikke her, men resultatet er disse tre ligninger (\cite[s.80-81]{compflow}):
$$
\begin{align}
    \frac{T_0}{T} = 1 + \frac{\gamma - 1}{2} M^2 \nonumber \\\
    \frac{p_0}{p} = \left(1 + \frac{\gamma - 1}{2} M^2\right)^\frac{\gamma}{\gamma - 1} \nonumber \\\
    \frac{\rho_0}{\rho} = \left(1 + \frac{\gamma - 1}{2} M^2\right)^\frac{1}{\gamma - 1} \nonumber
\end{align}
$$

---

## Forsøg

I dette afsnit opstilles et forsøg til at efterprøve teorien udledt i forrige afsnit.

### Opstilling

Opstillingen består af en "vindtunnel"\ med to forskellige tværsnitsarealer, et tværsnit af hvilken ses på Figur \ref{fig:crossection}.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Tværsnit.png}
    \caption{Tværsnit af "vindtunnelen" i forsøgsopstillingen. Modellen er lavet i Autodesk Fusion 360.}
\end{figure}
Tværsnittet er cirkulært, og har radius på henholdsvis
$$
\begin{align}
    r_1 = 3mm \nonumber \\\
    r_2 = 7mm \nonumber
\end{align}
$$
Det giver tværsnitsarealer på:
$$
\begin{align}
    A_1 = 2.829 \cdot 10^{-5} m^2 \nonumber \\\
    A_2 = 15.39 \cdot 10^{-4} m^2 \nonumber
\end{align}
$$
Forholdet mellem disse arealer er
$$
\begin{align}
    \frac{A_2}{A_1} \approx 5.44 \nonumber
\end{align}
$$
Enden af røret med lavere tværsnitsareal er åbent ud mod atmosfæren, og enden med højere tværsnitsareal er forbundet til en tryktank via en slange. Vindtunellen er et lille 3D printet rør af PETG plastik i to stykker. Der er boret et lille hul i siden af hver sektion, for at tryksensorer kan måle trykket, og at temperatursensorer kan placeres i strømmen. Rørenes samling er konisk for at kunne få god tætlukning. Vindtunellen er omsluttet af rør i støbejern, ca. som vist på Figur \ref{fig:pipescrossec}.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Rør med tværsnit.png}
    \caption{Tværsnit af vindtunnelen overlagt et billede af den ydre struktur af opstillingen.}
\end{figure}
Formålet med denne struktur er flerfoldigt. Metalrørenes ene formål er at holde trykket, sådan at plastikdelene ikke ser for høje trykforskelle over væggene. Dette er fordelagtigt da 3D printet plastik ikke er synderligt lufttæt, og derfor kan lække hvis trykforskellen bliver for stor. Desuden kan systemet se op imod 10 bar af tryk, hvilket plastikket tvivlsomt ville kunne holde til. Derved bliver plastikdelenes eneste formål at dirigere luftstrømmen, imens rørene holder trykket. Metalrørenes andet formål er lettere at kunne forbinde tryksensorer og trykslange, da disse bruger standardiserede gevind som skal strammes hårdt, og derfor er uegnede til plastik. \\\\
Imellem de to T-stykker sidder en brystnippel. Pladsen mellem dennes indervæg og ydervæggen af plastikrøret er forseglet med 2-parts epoxylim, sådan at trykkene på hver side kan være forskellige, og luft ikke kan flyde udenom vindtunellen. Til hver af T-stykkerne er forbundet et andet T-stykke hvori der sidder en tryksensor og er passeret en termoelement igennem. Trykket inde i hver sektion skulle gerne være lig trykket i de respektive dele af vindtunellen. Det var planen at der skulle have været et termoelement i hver side, men som set på Figur \ref{fig:pipescrossec} er der kun i den ene, grunden til dette diskuteres senere.

### Kalibrering

Tryksensorerne er forsynet med 5V, og putter en spænding ud mellem 0.5V og 4.5V som afhænger lineært af trykket. En hjemmelavet datalogger baseret på en Arduino Nano (ATmega328P) microcontroller blev brugt til dataopsamling. For at få så akkurate målinger som muligt, blev sensorerne kalibreret individuelt. Dette blev gjort ved at forbinde sensorerne til en cykelpumpe, og pumpe dem op til forskellige tryk, hvorved Arduinoens rå ADC målinger blev skrevet ned. En lineær regression blev udført på disse data, hver med en $R^2$ værdi på over $0.999$. Kalibreringsdata og de fundne $a$ og $b$ værdier kan findes i Bilag \ref{app:calibrationdata}. \\\\
Termoelementerne blev læst med en Vernier LabQuest Mini med tilhørende Thermocouple sensor-moduler (\cite{vernierthermo}).

### Hypotese

\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Tværsnit.pdf}
    \caption{Tværsnit af vindtunnelen med relevante størrelser på. Subskript $1$ angiver størrelser i den store sektion, subskript $2$ er i den lille. $A_u$ er udstødningens tværsnitsareal, og $p_a$ er atmosfærens tryk.}
\end{figure}
På Figur \ref{fig:vindtunnel_figur} ses en skitse af vindtunellens tværsnit, med relevante størrelser angivet. Forsøgsopstillingen analyseres med den inkompressible og kompressible model for strømning, for at se hvad de to forudsiger. Da der er en lang slange med et relativt lavt tværsnitsareal mellem tryktanken og vindtunellen, kan det ikke antages at hvilevariablerne i tanken og vindtunellen er ens. Til gengæld er $A_1$ $5.44$ gange større end $A_2$, så det antages at fluiden bevæger sig langsomt nok i den store sektion, til at strømvariablerne er lig hvilevariablerne for resten af vindtunellen:
$$
\begin{align*}
    \rho_1 = \rho_0 \\\
    T_1 = T_0 \\\
    u_1 = 0 \\\
    p_1 = p_0
\end{align*}
$$
Det bemærkes desuden at udstødningsarealet er lig $A_2$:
$$
\begin{align}
    A_u = A_2 \nonumber
\end{align}
$$

#### Inkompressibel strøm

Antages at strømningen er inkompressibel kan volumenstrømmen beregnes med Ligning \ref{eq:incompvolpresrel}:
$$
\begin{align}
    \dot{V} = A_u \sqrt{2 \frac{p_0 - p_a}{\rho}} \nonumber
\end{align}
$$
Da fluiden er luft, kan en densitet ikke umiddelbart gives, men den kan antages at være lig hviledensiteten. Da hviletrykket og temperaturen måles under forsøget, kan densiteten findes med idealgasloven (Ligning \ref{eq:intensiveidealgaslaw}):
$$
\begin{align}
    \rho = \frac{p_0}{R T_0} \nonumber
\end{align}
$$
Dette indsættes for $\rho$:
$$
\begin{align}
    \dot{V} = A_u \sqrt{2 R T_0 \frac{p_0 - p_a}{p_0}} \nonumber
\end{align}
$$
Dette indsættes så i Ligning \ref{eq:incomppresarea} for at kunne beregne de teoretiske tryk i de to sektioner af vindtunellen. Først for den lille sektion:
$$
\begin{align}
    p_2 = p_0 - \rho \frac{\left(A_u \sqrt{2 R T_0 \frac{p_0 - p_a}{p_0}}\right)^2}{2 A_2^2} \Rightarrow \nonumber \\\
    p_2 = p_0 - \rho \frac{A_u^2 2 R T_0 \frac{p_0 - p_a}{p_0}}{2 A_2^2} \nonumber
\end{align}
$$
Da det lille tværsnitsareal er lig udstødningsarealet, går disse ud med hinanden:
$$
\begin{align}
    p_2 = p_0 - \rho R T_0 \frac{p_0 - p_a}{p_0} \nonumber
\end{align}
$$
$\rho$ erstattes igen med den ideelle gaslov:
$$
\begin{align}
    p_2 = p_0 - p_0 \frac{p_0 - p_a}{p_0} \Rightarrow \nonumber \\\
    p_2 = p_a \nonumber
\end{align}
$$
Det forventes at trykket i den lille sektion vil være lig det atmosfæriske tryk. Nu til den store sektion:
$$
\begin{align}
    p_1 = p_0 - \frac{p_0}{R T_0} \frac{\left(A_u \sqrt{2 R T_0 \frac{p_0 - p_a}{p_0}}\right)^2}{2 A_1^2} \Rightarrow \nonumber \\\
    p_1 = p_0 - \frac{p_0}{R T_0} \frac{A_u^2 2 R T_0 \frac{p_0 - p_a}{p_0}}{2 A_1^2} \Rightarrow \nonumber \\\
    p_1 = p_0 - p_0 \frac{p_0 - p_a}{p_0} \frac{A_u^2}{A_1^2} \Rightarrow \nonumber \\\
    p_1 = p_0 - (p_0 - p_a) \left(\frac{A_u}{A_1}\right)^2 \nonumber
\end{align}
$$
Fra vindtunellens geometri vides at $A_1 = 5.44 \cdot A_u$. Dette indsættes:
$$
\begin{align}
    p_1 = p_0 - (p_0 - p_a) \left(\frac{A_u}{5.44 \cdot A_u}\right)^2 \Rightarrow \nonumber \\\
    p_1 = p_0 - (p_0 - p_a) \frac{1}{5.44^2} \nonumber
\end{align}
$$
Brøken giver ca. $0.034$. Så længe $p_0$ ikke er meget større end $p_a$ er hele andet led meget tæt på 0, derved kan det ses at:
$$
\begin{align}
    p_1 \approx p_0 \nonumber
\end{align}
$$
Antagelsen om at tryk 1 og hviletrykket er ens holder altså rimeligt, så længe at det egentlige hviletryk ikke er alt for meget højere end det atmosfæriske tryk. \\
For at opsummere vil vi, ifølge modellen for inkompressibel strømning se at $p_2$ er konstant lig med atmosfærisk tryk og at $p_1$ er ca. lig med hviletrykket som falder under forsøget, som trykket i tanken falder.

#### Kompressibel strøm

Betragtes strømmen som kompressibel, skal det først findes ud af hvorvidt den er kvalt. Så længe strømmen ikke er kvalt antages det at $p_2 = p_a$. Det antages også at $p_1 = p_0$, derved kan skrives:
$$
\begin{align}
    \frac{p_1}{p_a} = \frac{p_0}{p_2} \nonumber
\end{align}
$$
Derfor kan det antages at strømmen er kvalt når trykforholdet mellem $p_1$ og $p_a$ er større end det kritiske forhold, per Ligning \ref{eq:criticalpres}:
$$
\begin{align}
    \frac{p_1}{p_a} \geq \left(\frac{2}{\gamma + 1}\right)^\frac{\gamma}{1 - \gamma} \label{eq:choked?}
\end{align}
$$
Så længe dette er sandt haves et konstant trykforhold:
$$
\begin{align}
    \frac{p_1}{p_2} = \left(\frac{2}{\gamma + 1}\right)^\frac{\gamma}{1 - \gamma} \nonumber
\end{align}
$$
For luft, med $\gamma = 1.4$ (\cite[s.82]{compflow}), er dette forhold lig
$$
\begin{align}
    \left(\frac{2}{1.4 + 1}\right)^\frac{1.4}{1 - 1.4} \approx 1.893 \nonumber
\end{align}
$$
Det forventes altså at forholdet mellem $p_1$ og $p_2$ er konstant, så længe at forholdet mellem $p_1$ og $p_a$ er større end det kritiske forhold. Herefter skulle de to forhold gerne følge hinanden.

### Fremgangsmåde

Testopstillingen blev sat fast i en skruestik og forbundet til en 325 liter tryktank med en lang slange. Tryksensorerne blev forbundet til Arduino-dataloggeren, og termoelementet til LabQuest Mini'en. Se Figur \ref{fig:opstilling}.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Opstilling.jpg}
    \caption{"Vindtunellen"\ sat op i en skruestik, med sensorer og trykslange forbundet. (Undskyld rodet).}
\end{figure}
Tanken blev pumpet fra 1 bar absolut tryk, til 10 bar absolut tryk. Det er bemærkelsesværdigt at stålrøret fra kompressoren til tanken blev så varmt at det var ubehageligt at holde på i mere end to sekunder. Umiddelbart efter tanken var pumpet op, blev dataopsamlingen startet, og tankens udgangsventil åbnet. Når en luftstrøm ikke længere kunne føles fra udstødningen, blev dataopsamlingen stoppet.

### Resultater og databehandling

De rå data kan findes i Bilag \ref{app:expdata}. På Figur \ref{fig:data_liny} kan det målte tryk ses, plottet over tid.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Data_liny.png}
    \caption{De rå tryk målt over tid.}
\end{figure}
Som det kan ses er der et signifikant trykfald igennem slangen, da $p_1$ i starten kun er omkring $5.5$ bar.\\\\
Trykkene og temperaturen er som bekendt målt med to forskellige dataloggere, så de starter ikke på samme tidspunkt, og målingerne er heller ikke lavet med samme frekvens. Først blev temperaturmålingernes tidspuntker forskudt, for at passe med trykmålingerne, og excels $xlookup$ funktion blev derefter brugt til at til give en temperatur til hver tryk-datapunkt, da disse blev målt med langt højere frekvens. Funktionen blev sat til at vælge temperaturen fra den sidste temperaturmåling der var taget, i forhold til trykmålingens tidspunkt. Den resulterende graf kan ses på Figur \ref{fig:data_temp}.
\begin{figure}[h!]
    \centering
    \includegraphics[width=\textwidth]{Temp.png}
    \caption{Temperaturen målt over tid.}
\end{figure} \\\\
Det kan allerede ses på Figur \ref{fig:data_liny} at $p_2$ ikke er konstant lig med standard atmosfærisk tryk, men starter ved omkring 3 bar, og falder så imod atmosfærisk tryk. Det betyder altså at den inkompressible model ikke passer her. Alligevel beregnes en teoretisk volumenstrøm og $p_1$. Disse er plottet, sammen med den målte $p_1$, på Figur \ref{fig:data_incomp}.
\begin{figure}[h!]
    \centering
    \includegraphics[width=\textwidth]{Exp_incomp.png}
    \caption{Målt og forudset tryk plottet sammen med volumenstrøm over tid. Bemærk at volumenstrømmen er plottet på den sekundære akse.}
\end{figure}
Som det kan ses, passer det forudsete og målte tryk godt. Dette giver mening, da det målte tryk er brugt til at forudsige volumenstrømmen, som så er brugt til at forudsige det teoretiske tryk. Der kan derfor ikke konkluderes meget fra dette. \\\\
På Figur \ref{fig:data_comp} er forholdet mellem $p_1$ og henholdsvis $p_2$ og $p_a$ plottet. Desuden er det indikeret hvorvidt Ligning \ref{eq:choked?} er opfyldt.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Exp_comp.png}
    \caption{Trykforholdene $\frac{p_1}{p_a}$ og $\frac{p_1}{p_2}$ plottet sammen med forudsigelsen om hvorvidt strømmen er kvalt eller ej, over tid. Når Ligning \ref{eq:choked?} er opfyldt antager "Kvalt?"\ værdien 1, ellers er den 0.}
\end{figure}
Som forventet holder trykforholdet $\frac{p_1}{p_2}$ sig konstant i starten, med et gennemsnit over den flade del på $1.86$. Det begynder at falde lidt før trykforholdet mellem $p_1$ og $p_a$ når under den kritiske værdi, men det kan ses at de to forhold herefter følges ad nogenlunde.

### Diskussion af forsøget

Som diskuteret passer modellen for inkompressibel strømning slet ikke på dette forsøg. Modellen for kompressibel strømning passer dog nogenlunde. Det målte trykforhold har en relativ afvigelse fra den teoretiske værdi på:
$$
\begin{align}
    \frac{1.86 - 1.893}{1.893} = -1.74\% \nonumber
\end{align}
$$
Denne afvigelse er lille, men kunne have været endnu mindre hvis f.eks $A_1$ havde været større, da forholdene så havde været tættere på hvileforholdene. Modellen er desuden meget forsimplet, da den antager at farten er det samme over hele tværsnittet. I virkeligheden er dette ikke tilfældet, da friktion med væggen vil få fluiden tæt på denne til at bevæge sig langsommere. 3D print har relativt ru overflader, da de er bygget op af mange individuelle lag. Strømmen i forsøget løb på tværs af disse lag, så det kunne forestilles at denne rughed bidrager til friktionen. Figur \ref{fig:ansyssim} viser et tværsnit af tunnellen, simuleret i Ansys Fluent, med følgende værdier:
$$
\begin{align*}
    p_1 = 7 atm \\\
    t_1 = 20^\circ C \\\
    p_a = 1 atm
\end{align*}
$$
Farverne viser hvad det lokale Mach tal er. Jeg er ikke en ekspert i at bruge programmet, så værdierne er måske ikke helt præcise, tros dette kan det ses at Machtallet ikke er konstant igennem den snævre del, da det ligger omkring $0.6$ i starten og gradvist stiger imod 1. Det kan endda ses at det kommer helt op på omkring $1.2$ lige ved udstødningen. Desuden kan et grænselag tæt på væggen, hvor luften bevæger sig langsommere, ses.
\begin{figure}[ht]
    \centering
    \includegraphics[width=\textwidth]{Tunnel.png}
    \caption{Et tværsnit af tunnellen, simuleret i Ansys Fluent. Farver viser det lokale Mach tal.}
\end{figure}
Trykket måles omkring midten af den snævre sektion, så det kan forventes at luften ikke bevæger sig med Mach $1$ her, selvom det nok er højere end Mach $0.6$. Det faktum at $p_1$ ikke helt er lig hviletrykket, og at strømmen ikke bevæger sig med Mach $1$ i hele den snævre del bidrager sandsynligvis begge til at det observerede trykforhold er lavere end forventet, og at det målte trykforhold begyndte at falde før forventet. \\\\
Grunden til at det ene termoelement blev fjernet, var fordi det blev så koldt at der formede is på overfladen af den under test-kørslerne, hvilket faktisk endte med helt at blokkere strømmen. Trykforholdet var $1.86$, og den højeste målte temperatur under kørslen ca. $13.5^\circ C$, så pr. Ligning \ref{eq:isentropicprestemp} har den teoretiske temperatur været:
$$
\begin{align}
    T_2 = T_1 \left(\frac{p_2}{p_1}\right)^\frac{\gamma - 1}{\gamma} \\\
    T_2 = (13.5 + 273.15)K \left(\frac{1}{1.86}\right)^\frac{1.4 - 1}{1.4} \approx 240K
\end{align}
$$
Det svarer til ca. $-33^\circ C$. Med fugtigheden i luften er det klart at der blev formet is på overfladen. Selv uden termoelementet i strømmen, fløj små isklumper ud af udstødningen med høj fart, hvilket kunne mærkes med en hånd placeret i strømmen. De er sandsynligvis begyndt at forme på indersiden i den snævre sektion, men er blevet revet væk af lufstrømmen inden de blev for store. \\\\
Nogle højhastigheds-vindtuneller bruger gas opvarmet til mange-hundrede grader hviletemperatur, for at gassen ikke skal kondensere til væske. F.eks en vindtunnel ved The University of Texas at San Antonio, som har en vindtunnel der kan nå op på Mach 7.2, med en hviletemperatur på $700K$ ($\sim 427^\circ C$).

### Konklusioner fra forsøget

Det kan konkluderes fra forsøget at forudsigelserne fra modellen for inkompressibel strømning ikke passer til en gasstrøm med høje trykforhold. Modellen for kompressibel strømning passer heller ikke perfekt, men med en relativ afvigelse mellem det forudsete og målte trykforhold på $-1.74\%$ passer den meget bedre. Forsøget kunne være gentaget med væske i stedet for en gas, for at validere om den inkompressible model ville passe bedst her.

---

## Diskussion

Modellen for kompressibel strømning udledt i projektet er baseret på en del antagelser for at forsimple ligningerne, sådan at de kan løses. Det antages at strømmen er adiabatisk, altså at der ikke tilføjes varme, at den er reversibel sådan tryk og densitet kan beregnes, at der ikke er friktion med vægen, at fluiden ikke har intern friktion (viskositet), at hastigheden altid er konstant over, og normal til tværsnittet, selv i sektioner hvor tværsnittet ændrer sig, at andre strømningsvariabler også er konstante over tværsnittet og at gassen er ideel. Det virker umiddelbart som meget restriktivt og langt fra virkeligheden, men som set passer modellens forudsigelser alligevel rimeligt på data fra virkelige strømninger. Eksperimentet brugte et relativt langt og tyndt rør med en ru overflade, og forudsigelserne passede stadig nogenlunde. For eksempel er en raketmotor ofte langt større, og er lavet af metal med en glat indre overflade. Så længe problemerne ikke involverer lange, tynde rør og holder sig indenfor et tryk- og temperaturområde hvor gassen kan antages at være ideel, med konstante varmekapaciteter og adiabatkonstant, passer modellen altså rimelig godt. \\\\
Selv hvis modellen ikke giver en komplet beskrivelse af virkeligheden, kan den stadig bruges til at forstå hvorfor raketdyser er formet som de er, og den kan bruges til at informere designbeslutninger. F.eks kan modellen bruges til at estimere hvad dimensionerne af en raketmotor skal være ud fra ønskede design-specifikationer, inden CFD programmer som f.eks Ansys Fluent bruges til at lave mere detaljerede analyser og optimeringer. Programmer som dette bruger diverse numeriske metoder til at løse bevarelsesligningerne på differential form i 3 dimensioner for komplicerede strømningsfelter og kan også håndtere solidt geometri i felterne, varmetilførsel, viskositet, etc. De er velegnede til at simulere strømning omkring f.eks flyvinger og andre mere komplekse former, noget som ville være ekstremt komplekst og ofte umuligt at løse analytisk. \\\\
Mange af koncepterne diskuteret i modellen, som f.eks hvileforhold, Machtal, konstant masse- og energibevarelse og kvalning kan også bruges til at forstå hvordan andre ting involverende fluider fungerer. F.eks en aksial kompressor fra en jetmotor eller en turbosnegl i en bil, hvor roterende blade udfører arbejde på gassen for at levere den energi der skal til for at komprimere den og derved ændrer hvileentalpien (\cite{compthermo}).
