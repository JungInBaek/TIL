@startuml
Calculator --> AbstractOperation
AbstractOperation <|-- AddOperation
AbstractOperation <|-- SubstractOperation
AbstractOperation <|-- MultiplyOperation

class Calculator {
  + calculate(operation : AbstractOperation, firstNumber : int, secondNumber : int) : int
}

abstract class AbstractOperation {
  + operate(firstNumber : int, secondNumber : int) : int
  + isInvalidNumber(firstNumber : int, secondNumber : int) : boolean
}

class AddOperation {
  + operate(firstNumber : int, secondNumber : int) : int
}

class SubstractOperation {
  + operate(firstNumber : int, secondNumber : int) : int
}

class MultiplyOperation {
  + operate(firstNumber : int, secondNumber : int) : int
}
@enduml