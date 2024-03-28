# O.S 1 Drill Checker

Graphs are created with [Mermaid](https://mermaid.js.org/).
This is the basic UML and planning of this project.
We will be using Docker and Python, to check the student assigments.

```mermaid

---
title: Student
---
classDiagram
  
    class Student{
        self.student_dir
        self.compilation_errors = []
        self.warning_messages = []
        self.test_results = []
        self.grade = 100 
        self.extraction_penalty = 0 
        self.catched_errors = []
        self.memory_leaks = []
        self.readme_content = self.read_readme()
        self.output = []
        self.source_headers = 
    }
   

```

```mermaid



graph TD;

   
    subgraph Run_Student
        Compile[Compile]

        Valgrind[Valgrind]

        Run[Run]

        Tests[Tests]

        Runner[Runner]

    end
    subgraph Command_line

        CLI[CLI]

    end
    subgraph Configuration
        
        UserInputConfig[User Input Config]
        ConfigParser[Config Parser]

        ConfigData[Config Data]


    end
    subgraph ConfigInput
        Input[Input]

    end
    ConfigFile[Config File JSON/XML/YAML]
    subgraph Utilities
        CleanNames[Clean Names]

        Extraction[Extraction]

        Reverse[Reverse]



    end
    subgraph Logging_Unit

        Log[Log]

    end
    Input --UserInput--> UserInputConfig
    Input --FileInput--> ConfigParser

    Summarize[Summarize]
    CLI --> Input
    UserInputConfig --> ConfigData
    ConfigParser --> ConfigData
    ConfigParser --> ConfigFile
    
    CLI --> CleanNames
    ConfigData <--> CLI
    CLI --> Run
    CLI --> Summarize
    CLI --> Extraction
    CLI --> Reverse
    Log <--> CLI

    Run --> Compile
    Run --> Valgrind
    Run --> Runner
    Run --> Tests
    
    Extraction --> Log
    Run --> Log
    Compile --> Log
    Valgrind --> Log
    Runner --> Log
    Tests --> Log

    style CLI fill:#f9f,stroke:#333,stroke-width:4px
    style Log fill:#bbf,stroke:#f66,stroke-width:2px,stroke-dasharray: 5, 5

```