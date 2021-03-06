Assume the following input text.
```
We see
%
\begin{itemize}
\item that all is acceptable andx
\item that it can be improved.
\end{itemize}

Thus, with a constant $C$ and a domain $\Omega$,
%
\begin{align}
\mu &= f(x) \quad\text{for all } \mu\in\Omega, \notag \\
x   &= \begin{cases}
        0 & \text{for} \ y>0 \\
        1 & \text{in case} y\le 0.
            \end{cases}     \label{lab}
\end{align}
```
Using option --lang en, one gets the following Python script output.
```
We see
  that all is acceptable andx
  that it can be improved.

Thus, with a constant B and a domain C,
  U  equal V for all W, 
  X  equal Y for Z 
  Z in caseU. 
```
With the filter from the Bash script shell.sh, the typo 'andx' will be
related to line 4.
The problems in the equation (missing comma leads to word repetition,
missing space to spelling error) will be related to line 12+ and 14+,
respectively (line 12 is \\begin\{cases\}).

Here is the output of shell.sh. Line numbers in \[\] brackets have been
added by the filter in variable \$repl\_lines of the Bash script.
```
1.) Line 2 [4], Rule ID: MORFOLOGIK_RULE_EN_GB
Message: Possible spelling mistake found
Suggestion: and; Andy; and x
We see   that all is acceptable andx   that it can be improved.  Thus, with a con...
                                ^^^^                                             

2.) Line 7 [12+], Rule ID: ENGLISH_WORD_REPEAT_RULE
Message: Possible typo: you repeated a word
Suggestion: Z
...C,   U  equal V for all W,    X  equal Y for Z    Z in caseU.  
                                                ^^^^^^            

3.) Line 8 [14+], Rule ID: MORFOLOGIK_RULE_EN_GB
Message: Possible spelling mistake found
Suggestion: case; cases; Casey; cased; CSEU; case U
...ual V for all W,    X  equal Y for Z    Z in caseU.  
                                                ^^^^^   
Time: 2917ms for 3 sentences (1.0 sentences/sec)
```
