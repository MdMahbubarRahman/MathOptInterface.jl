```@meta
CurrentModule = MathOptInterface
DocTestSetup = quote
    using MathOptInterface
    const MOI = MathOptInterface

    # For compatibility with both Julia 1.0.5 and 1.5.2
    # Upon the Julia LTS version becoming 1.6, these imports could be dropped,
    # and all ScalarAffineTerm and VariableIndex instances in doctests below
    # could be replaced with MOI.ScalarAffineTerm and MOI.VariableIndex
    # Check discussion at PR 1184: https://github.com/jump-dev/MathOptInterface.jl/pull/1184#discussion_r515300914
    import MathOptInterface.ScalarAffineTerm
    import MathOptInterface.VariableIndex
end
DocTestFilters = [r"MathOptInterface|MOI"]
```

# Bridges

## AbstractBridge API

```@docs
Bridges.AbstractBridge
Bridges.added_constrained_variable_types
Bridges.added_constraint_types
get(::Bridges.AbstractBridge, ::NumberOfVariables)
get(::Bridges.AbstractBridge, ::ListOfVariableIndices)
get(::Bridges.AbstractBridge, ::NumberOfConstraints)
get(::Bridges.AbstractBridge, ::ListOfConstraintIndices)
Bridges.needs_final_touch
Bridges.final_touch
```

## Constraint bridge API

```@docs
Bridges.Constraint.AbstractBridge
supports_constraint(::Type{<:Bridges.Constraint.AbstractBridge}, ::Type{<:AbstractFunction}, ::Type{<:AbstractSet})
Bridges.Constraint.concrete_bridge_type
Bridges.Constraint.bridge_constraint
Bridges.Constraint.AbstractFunctionConversionBridge
Bridges.Constraint.SingleBridgeOptimizer
Bridges.Constraint.add_all_bridges
Bridges.Constraint.FlipSignBridge
Bridges.Constraint.AbstractToIntervalBridge
Bridges.Constraint.SetMapBridge
```

## Objective bridge API

```@docs
Bridges.Objective.AbstractBridge
Bridges.Objective.supports_objective_function
Bridges.set_objective_function_type
Bridges.Objective.concrete_bridge_type
Bridges.Objective.bridge_objective
Bridges.Objective.SingleBridgeOptimizer
Bridges.Objective.add_all_bridges
```

## [Variable bridge API](@id ref_variable_bridges)

```@docs
Bridges.Variable.AbstractBridge
Bridges.Variable.supports_constrained_variable
Bridges.Variable.concrete_bridge_type
Bridges.Variable.bridge_constrained_variable
Bridges.Variable.SingleBridgeOptimizer
Bridges.Variable.add_all_bridges
Bridges.Variable.FlipSignBridge
Bridges.Variable.SetMapBridge
Bridges.Variable.unbridged_map
```

## AbstractBridgeOptimizer API

```@docs
Bridges.AbstractBridgeOptimizer
Bridges.bridged_variable_function
Bridges.unbridged_variable_function
Bridges.bridged_function
Bridges.supports_constraint_bridges
Bridges.recursive_model
```

## LazyBridgeOptimizer API

```@docs
Bridges.LazyBridgeOptimizer
Bridges.full_bridge_optimizer
Bridges.ListOfNonstandardBridges
Bridges.add_bridge
Bridges.remove_bridge
Bridges.has_bridge
Bridges.print_active_bridges
Bridges.print_graph
Bridges.debug_supports_constraint
Bridges.debug_supports
```

## [SetMap API](@id constraint_set_map)

```@docs
Bridges.map_set
Bridges.inverse_map_set
Bridges.map_function
Bridges.inverse_map_function
Bridges.adjoint_map_function
Bridges.inverse_adjoint_map_function
```

## Bridging graph API

```@docs
Bridges.Graph
Bridges.VariableNode
Bridges.ConstraintNode
Bridges.ObjectiveNode
Bridges.Edge
Bridges.ObjectiveEdge
Bridges.add_node
Bridges.add_edge
Bridges.set_variable_constraint_node
Bridges.bridge_index
Bridges.is_variable_edge_best
```
