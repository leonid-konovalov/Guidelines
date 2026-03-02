### Modules

* In the usual case, keep each class in a separate module with the same name.
  E.g., ``RiskFactor`` class must be exclusively in ``RiskFactor.py`` module.

### Testing

* Write a unit test for each non-trivial class method.
* Use ``unittest`` library.
* Use one unit test class for each class under test.
* Name a test class by adding 'Test' to the class under test name (e.g.,
  ``RiskFactorTest`` for ``RiskFactor`` class).
* Place stub classes for a test in the same module before the test class.

### Typing

* Specify parameter and return types explicitly, unless ```None``` is returned:
  ```
  # Correct:
  def getFactorValue(self, scopeAssignment: VariableAssignment) -> float:
      pass
  ```
  ```
  # Wrong:
  def getFactorValue(self, scopeAssignment):
      pass
  ```
  ```
  # Correct:
  def update(self):
      pass
  ```
  ```
  # Wrong:
  def update(self) -> None:
      pass
  ```
  ###### Rationale
    * Explicit return types enable better type hinting, so errors may be
      detected
      earlier.
    * Syntax separation between functions and procedures makes the code more
      readable.


* Where applicable, use ``typing`` library:
  ```
  from typing import Set, Union
  
  def getVariableSupport(scopeVariable: Union[Variable, str]) -> Set[float]:
      pass
  ```

### Code style

##### General guidelines

Follow PEP8 when it does not contradict the guidelines below.

##### Case

* Use CamelCase for class, type, package, and module names:
  ```
  # Correct:
  from typing import TypeVar
  
  from GrapicalModels.Factor import Factor 
  
  ValueType = TypeVar('ValueType')
  
  
  class DiscreteFactor(Factor):
      pass
  ```

* Use lowerCamelCase for function, method, parameter, member and variable
  names:
  ```
  # Correct: 
  def getNormalizedValue(self, scopeVariable: str) -> float:
     assignedValue = self.__values[scopeVariable]
     return assignedValue / self.__total
  ```    

* For imported names, snake_case is admissible.

###### Rationale

Camel case is very common in UML. Use of different cases in design
and implementation files would be expensive and error-prone. Implementation can
be done in different languages, while design is practically not.

##### Line wrapping

* Limit all lines to a maximum of 79 characters (PEP8).

* If a declaration or call cannot fit into one line,
  place each parameter on a separate line:
  ```
  # Correct:
  def addVariableConditionalDistribution(
      self, 
      variableName: str, 
      newConditionalDistribution: Factor
  ):
      pass
  ```
  ```
  # Correct:
  newFactor = factorCreator.createCustomDiscreteFactor(
      scope=["A", "C"],
      scopeAssignments=[{"A": 0, "C": 0}]
      values=[1]
  )   
  ```
  ```    
  # Wrong:
  def addVariableConditionalDistribution(
      self, variableName: str, 
      newConditionalDistribution: Factor
  ):
      pass
  ```
  ```
  # Wrong:
  newFactor = factorCreator.createCustomDiscreteFactor(
      scope=["A", "C"], scopeAssignments=[{"A": 0, "C": 0}], values=[1]
  )
  ```

* Do not place subcall parameters on separate lines, if they fit into one
  line:
    ```
    # Correct:
    newFactor = factorCreator.createCustomDiscreteFactor(
        scope=["A", "C"],
        assignments=getUniformAssignments(scope=["A", "C"], valueCount=2),
        values=[1, 2, 4, 8]
    ) 
    ```
    ```
    # Wrong:
    newFactor = factorCreator.createCustomDiscreteFactor(
        scope=["A", "C"],
        assignments=getUniformAssignments(
            scope=["A", "C"], 
            valueCount=2
        ),
        values=[1, 2, 4, 8]
    )
    ```

* If a conditional statement cannot fit into one line, wrap it as follows:
  ```
  # Correct:
  if (
      "." not in sourceFolderElementName
      and 
      "__" not in sourceFolderElementName
  ):
      pass
  ```
  ###### Rationale
    * Good readability.
    * Compatibility with PyCharm autoformatting.


* If an import statement cannot fit into one line,
  wrap it as follows:
  ```
  # Correct:
  from Graphs.DirectedEdgeNodeIteratorWrapper import \
      DirectedEdgeNodeIteratorWrapper
  ```

##### Indentation

* In multiline declarations and calls, use hanging indent with one indentation
  level for parameters:
  ```
  # Correct:
  def getConditionalDistribution(
      self,
      conditioning: VariableAssignment,
      independenceMap: DirectedGraph,
      observationDate: date
  ):
      result = self.__jointDistribution.getReducedFactor(
          conditioning=conditioning, 
          independenceMap=independenceMap,
          observationDate=observationDate
      )
  ```
  ```
  # Wrong:
  def getConditionalDistribution(
          self,
          conditioning: VariableAssignment,
          independenceMap: DirectedGraph,
          observationDate: date
  ):
      result = self.__jointDistribution.getReducedFactor(
              conditioning=conditioning, 
              independenceMap=independenceMap,
              observationDate=observationDate
      )
  ```

* Line up closing brace/bracket/parenthesis under the first character
  of a multiline construct:
  ```
  # Correct:
  result = self.__jointDistribution.getReducedFactor(
      conditioning=conditioning, 
      independenceMap=independenceMap,
      observationDate=observationDate
  )
  ```
  ```
  # Wrong:
  result = self.__jointDistribution.getReducedFactor(
      conditioning=conditioning, 
      independenceMap=independenceMap,
      observationDate=observationDate
      )
  ```
  ```
  # Wrong:
  result = self.__jointDistribution.getReducedFactor(
      conditioning=conditioning, 
      independenceMap=independenceMap,
      observationDate=observationDate)
  ```

* Do not increase indentation more than by one level:
  ```
  # Wrong:
  drift[index + 1] = drift[index] \
                        + difference / volatility[index]
  ```
  ```
  # Correct: 
  drift[index + 1] = drift[index] \
      + difference / volatility[index] ** 2
  ```
  ```
  # Correct: 
  drift[index + 1] = \
      drift[index] + difference / volatility[index] ** 2
  ```

##### Function and Method Arguments

* Use arg to call a function or method with one argument:
  ```
  # Correct:
  return factor.getValue({"X": 0, "Y": 1})
  ```

* Use kwargs to call a function or method with multiple arguments:
  ```
  # Correct:
  newFactor = factorCreator.createCustomDiscreteFactor(
      scope=["A", "C"],
      assignments=[{A: 1, C: 0}],
      values=[1]
  ) 
  ```
  ```
  # Wrong:
  newFactor = factorCreator.createCustomDiscreteFactor(
      ["A", "C"],
      [{A: 1, C: 0}],
      [1]
  ) 
  ```
* Do not use comma after the last argument:
  ```
  # Correct:
  newFactor = factorCreator.createCustomDiscreteFactor(
      scope=["A", "C"],
      assignments=[{A: 1, C: 0}],
      values=[1]
  ) 
  ```
  ```
  # Wrong:
  newFactor = factorCreator.createCustomDiscreteFactor(
      scope=["A", "C"],
      assignments=[{A: 1, C: 0}],
      values=[1],
  )
  ``` 

  ###### Rationale
  This Python feature is uncommon in other languages.

##### Naming

* Names should make code to be readable like natural language:
  ```
  # Correct:
  for scopeElement in distributionFactor.getScope():
     pass
  ```
  ```
  # Wrong:
  for var in df.getVars():
     pass
  ```

* Do not use single-letter variable names in loops. Use meaningful names
  instead:
  ```
  # Wrong:
  for i in range(covariance.shape[0]):
      for j in range(covariance.shape[1]):
          print(covariance[i, j])
  ```
  ```
  # Correct:
  for rowIndex in range(covariance.shape[0]):
      for columnIndex in range(covariance.shape[1]):
          print(covariance[rowIndex, columnIndex])
  ```

* Do not exclude vowels:
  ```
  # Wrong:
  idx = 64
  ```
  ```
  # Correct:
  index = 64
  ```

* Avoid use of abbreviations, unless ubiquitously used ones:
  ```
  # Correct:
  class DynamicBaysianNetwork(ProbabilisticGraphicalModel):
      pass
  ```
  ```
  # Wrong:
  class DBN(PGM):
      pass
  ```
  ```
  # Possible:
  # Domain experts almost always say 'CSA', 'Credit Support Annex' is uncommon
  class CSA:
      """
      Represents Credit Support Annex to ISDA master agreement.
      """
      pass
  ```

* Do not use an adjective or adverb as a variable name:
  ```
  # Wrong:
  restored = storage.getObject(key)
  ```
  ```
  # Correct:
  restoredObject = storage.getObject(key)
  ```

* In most cases variable and parameter names must capture their roles,
  not types:
  ```
  # Correct:
  def addScopeElement(newScopeElement: Variable):
      pass
  ```
  ```
  # Usually wrong:
  def addScopeElement(variable: Variable):
      pass
  ```
* A variable name is generally not needed if it is used only once:
  ```
  # Wrong:
  factorValue = distributionFactor.getValue({A: 0, B: 1})
  return getPayoff(underlyingValue=factorValue, observationDate=valueDate)
  ```
  ```
  # Correct:
  return getPayoff(
     underlyingValue=distributionFactor.getValue({A: 0, B: 1}), 
     observationDate=valueDate
  )
  ```

##### Imports

* Group imports according to PEP8.

* Sort imports case-sensitively.
* Sort plain and "from" imports separately.
* Sort names in "from" imports.

  ```
  # Correct:
  import copy
  import zipapp
  from typing import Callable, List
  from unittest import TestCase
  
  import QuantLib
  import pandas
  
  from Notification.Observer import Observer
  ```
  ```
  # Wrong:
  import copy
  from unittest import TestCase
  from typing import Callable, List
  import zipapp
  
  import pandas
  import QuantLib
  
  from Notification.Observer import Observer
  ```

  ###### Rationale
    * Ordered imports are easier to read and edit.
    * Merge conflicts are avoided.


* Erase unused imports.

* Avoid renaming and abbreviation:
  ```
  # Correct: 
  import pandas
  ```
  ```
  # Wrong:
  import pandas as pd
  ```
  ###### Rationale
  Do not burden a reader by the context knowledge. E.g.,
  'pd' might stand for 'pandas' or 'probability of default'
  in different contexts.

##### Documentation

* Write documentation in English.

* Docstrings are not mandatory, with well naming they can be often omitted.
  ```
  # Possible:
  def getSpotExchangeRate(
      self,
      foreignCurrency, str, 
      domesticCurrency: str,
      observationDate: date
  ) -> float:
      pass
  ```
  ```
  # Wrong:
  def getRate(self, fc: str, dc: str, dt: date):
      """
      :param fc: foreign currency code
      :param dc: domestic currency code
      :return: spot fcdc exchange rate
      """
  ```

  ###### Rationale
  Docstrings are difficult to maintain, they are not updated automatically
  in contrast to function, method and variable names.


* Add only valuable docstrings. E.g., the docstrings below add nothing
  to the method signature, therefore they must be omitted or replaced:
  ```
  # Wrong:
  def getModelPrice(self, pricingDate: date, pricingCurrency: str) -> float:
      """
      :param pricingDate: date to calculate price on
      :param pricingCurrency: returned price currency
      :return: instrument price calclulated with model
      """

      pass
  ```

### Exceptions

* Catch only specific exceptions:
  ```
  # Wrong:
  try:
      return storage.getObject(key)
  except Exception:
      pass
  ```
  ```
  # Correct:
  try:
      return storage.getObject(key)
  except KeyError:
      pass 
  ```
  
  ###### Rationale
  Swallowed exceptions result in hard-to-debug code.
