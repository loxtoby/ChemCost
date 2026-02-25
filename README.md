# ChemCost

ChemCost is a calculation-driven, single-page web application designed for modeling and costing multi-step pharmaceutical synthesis processes. It allows users to define raw materials, equipment, and a sequence of synthetic operations to automatically generate mass flow simulations, cost breakdowns, and scheduling timelines. ChemCost relies on rule-of-thumb heuristics to auto-derive some durations and quantities useful for  early-stage scoping. Users build processes using natural-language template sentences (e.g., additions, reactions, filtrations). The engine computes comprehensive batch-level cost breakdowns, factoring in raw materials (unit cost × quantity), equipment usage (hourly rate × duration), and labor (department rate × duration).

## How it works

All application state lives in a single, normalized in-memory store. An active session-level undo/redo stack captures state modifications without permanent persistence. The engine relies on pure functions to process operations via topological sorting and actively resolves durations, accumulates costs, checks mass balances, and navigates Directed Acyclic Graph (DAG) topologies for step dependencies. The application operates entirely without a backend database. Projects are saved and loaded strictly via versioned JSON files, featuring a built-in migration system for forward compatibility.
