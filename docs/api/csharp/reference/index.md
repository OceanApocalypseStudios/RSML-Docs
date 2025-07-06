# API Reference _(C\#)_
The API reference for RSML in C# is organized by **namespace** and then **class**.

## Overview
* [`RSML`](RSML/index.md)
    - [`RSDocument`](RSML/RSDocument.md)
        - [`#!c# EvaluateDocument()`](RSML/RSDocument.md#c-evaluatedocument)
        - [`#!c# EvaluateDocument(string lineSeparation)`](RSML/RSDocument.md#c-evaluatedocumentstring-lineseparation)
        - [`#!c# EvaluateDocument(bool expandAny, string? lineSeparation = null)`](RSML/RSDocument.md#c-evaluatedocumentbool-expandany-string-lineseparation--null)
        - [`#!c# EvaluateDocument(string customRid, string? lineSeparation = null)`](RSML/RSDocument.md#c-evaluatedocumentstring-customrid-string-lineseparation--null)
        - [`#!c# EvaluateDocument(string customRid, bool expandAny, string? lineSeparation = null)`](RSML/RSDocument.md#c-evaluatedocumentstring-customrid-bool-expandany-string-lineseparation--null)
        - [`#!c# LoadRSMLFromFile(string filepath)`](RSML/RSDocument.md#c-loadrsmlfromfilestring-filepath)
        - [`#!c# LoadRSMLFromFileAsync(string filepath)`](RSML/RSDocument.md#c-loadrsmlfromfileasyncstring-filepath)
        - [`#!c# LoadRSMLFromFileIntoDocument(string filepath)`](RSML/RSDocument.md#c-loadrsmlfromfileintodocumentstring-filepath)
        - [`#!c# NewFromFile(string filepath)`](RSML/RSDocument.md#c-newfromfilestring-filepath)
        - [`#!c# RSDocument(string rsml)`](RSML/RSDocument.md#c-rsdocumentstring-rsml)
        - [`#!c# RSDocument(StringReader reader)`](RSML/RSDocument.md#c-rsdocumentstringreader-reader)
        - [`#!c# RSDocument(RSParser parser)`](RSML/RSDocument.md#c-rsdocumentrsparser-parser)
        - [`#!c# SaveRSMLToFile(string filepath)`](RSML/RSDocument.md#c-saversmltofilestring-filepath)
        - [`#!c# ToString()`](RSML/RSDocument.md#c-tostring)

* `RSML.Exceptions`
    - `ImmutableActionException`
        - `#!c# ImmutableActionException()`
        - `#!c# ImmutableActionException(string message)`
        - `#!c# ImmutableActionException(string? message, Exception? innerException)`
    - `RSMLRuntimeException`
        - `#!c# RSMLRuntimeException()`
        - `#!c# RSMLRuntimeException(string message)`
        - `#!c# RSMLRuntimeException(string? message, Exception? innerException)`
    - `UndefinedActionException`
        - `#!c# UndefinedActionException()`
        - `#!c# UndefinedActionException(string message)`
        - `#!c# UndefinedActionException(string? message, Exception? innerException)`
    - `UndefinedSpecialException`
        - `#!c# UndefinedSpecialException()`
        - `#!c# UndefinedSpecialException(string message)`
        - `#!c# UndefinedSpecialException(string? message, Exception? innerException)`

* `RSML.Parser`
