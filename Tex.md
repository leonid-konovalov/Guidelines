### Document Style

##### Section and Subsection Heads

* Capitalize only first word, except for the proper nouns. E.g.:

  > 1.1. Derivation of the second price decomposition

  > 1.2. The generalized Feynman–Kac equation

  ###### Rationale
  Allowed by [AMS Style Guide](
    https://www.ams.org/publications/authors/AMS-StyleGuide-online.pdf
  ) and consistent with the Russian language.

##### Formulas

* Use '1' to denote an indicator.
  ```
  % Correct:
  $1\{x > 0\}$
  ```

* If a formula does not fit into one line, try to split it and align vertically
  * signs of comparison,
  * other signs. 
  ```
  % Preferrable:
  \begin{equation*}
      \begin{split}
          dD_t X_t 
          &= D_t dX_t + X_t dD_t + dD_t dX_t \\
          &= D_t (dX_t - r_t X_t dt)
      \end{split}
  \end{equation*}
  ```

##### Bibliography

* Use full first names when citing, e.g.:
  > Steven E. Shreve. Stochastic Calculus for Finance II. Springer, 2004.


### Code style

##### Line wrapping

* Limit all lines to a maximum of 79 characters.
* Use non-breaking space with reference:
  ```
  % Correct:
  From~\eqref{eq:priceProcessFormula} we obtain
  ```
  ```
  % Wrong:
  From \eqref{eq:priceProcessFormula} we obtain
  ```
##### Paragraphs

* Separate paragraphs by a blank line, not by ```\par``` command.

##### Indentation

* Use one indentation level to separate 
  * logical text elements
    * section and subsection content,
  * code inside an environment.
  ```
  % Correct:
  \subsection{General stochastic volatility model}

      Consider the next general stochastic volatility model. Suppose that the 
      underlying price $S$ and its instantaneous variance $v$ satisfy the
      equations below.
  ```
  ```
  % Correct:
  \begin{itemize}
      \item $\alpha$,
      \item $\beta$.
  \end{itemize}
  ```
  ```
  % Correct:
  \begin{equation*}
      \begin{split}
          dD_t X_t 
          &= D_t dX_t + X_t dD_t + dD_t dX_t \\
          &= D_t (dX_t - r_t X_t dt)
      \end{split}
  \end{equation*}
  ```
##### Blank Lines

* Surround with blank lines the following commands:
  * ```\section```,
  * ```\subsection```.
  ```
  % Correct:
  \section{Stochastic volatility models}
  
    In this section we derive the hedging error decomposition for a number of 
    popular stochastic volatility models. 
  
    \subsection{General stochastic volatility model}

        Consider the next general stochastic volatility model.
  ```

##### Tables

* Put each table row code on a separate line. Wrap long cell code as follows:
  ```
  % Correct:        
  \begin{table}
      \begin{tabular}{|c|c|c|c|}
          \hline
              Сущность / термин
              & Описание \\
          \cline{3-4}
              &
              & \textbf{Лекции}
              & Соглашение с контрагентом о выплатах и / или поставке 
                  активов. Делятся на _срочные_ и _spot_ сделки(с выплатой / 
                  поставкой до двух дней). В контексте расчет контрагентского 
                  риска рассматривают срочные сделки. \\
          \hline
      \end{tabular}
  \end{table}
  ```

##### Formulas

* Use ```equation``` and ```equation*``` environments for non-inline formulas:
  
  ```
  % Correct:
  \begin{equation}
      \int_{-\infty}^{\infty} f(x) dx = 1.
  \end{equation}
  ```
  ```
  % Wrong:
  $$
      \int_{-\infty}^{\infty} f(x) dx = 1.
  $$
  ```
  ```
  % Wrong:
  \[
      \int_{-\infty}^{\infty} f(x) dx = 1.
  \]
  ```  

  ###### Rationale
  Use simular constructions for numbered and unnumbered equations.


* Place a subscript before a superscript:
  ```
  % Correct:
  X_t^2
  ```
  ```
  % Wrong:
  X^2_t
  ```
  ###### Rationale
  Follow natural reading order for the variable powers.


##### Labels

* Use one of the next prefixes according to the labeled element type:
  * theorem,
  * lemma,
  * equation,
  * figure,
  * table.
  
* Separate label prefix by a colon.

* Make readable labels that clearly identify the element given a reasonable
  amount of context.
    ```
    % Correct: 
    \label{lemma:DiscountedOptionPriceDynamics}
    ```
* Use UpperCamelCase after a prefix.
    ```
    % Wrong: 
    \label{lemma:discountedOptionPriceDynamics}
    ```
    ```
    % Wrong: 
    \label{lemma:discounted_option_price_dynamics}
    ```
* Do not repeat a prefix.
    ```
    % Wrong: 
    \label{lemma:DiscountedOptionPriceDynamicsLemma}
    ```
* Use local labels to make labels compact:
    ```
    % Recommended:
    \subsection{Hedging error decomposition without recalibration}
  
        \begin{equation} 
            \labellocal{equation:DiscountedOptionPrice}
            dD_t X_t = \Delta_t d D_t S_t.
        \end{equation}
        Subtract~\reflocal{equation:DiscountedOptionPrice} from the discounted 
        financial result.
    ```
    ```
    % Not recommended:
    \subsection{Hedging error decomposition without recalibration}
  
        \begin{equation} 
            \label{equation:DiscountedOptionPriceNoRecalibration}
            dD_t X_t = \Delta_t d D_t S_t.
        \end{equation}
        Subtract~\ref{equation:DiscountedOptionPriceNoRecalibration} from the 
        discounted financial result.
    ```      

* Use compact notation for one half:
  ```
  % Correct: 
  \frac12
  ```
  ```
  % Wrong:
  \frac12
  ```
