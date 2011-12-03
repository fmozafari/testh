[![Actions Status](https://github.com/fmozafari/angel/workflows/Linux%20CI/badge.svg)](https://github.com/fmozafari/angel/actions)
[![Actions Status](https://github.com/fmozafari/angel/workflows/MacOS%20CI/badge.svg)](https://github.com/fmozafari/angel/actions)
[![Coverage Status](https://coveralls.io/repos/github/fmozafari/angel/badge.svg?branch=master)](https://coveralls.io/github/fmozafari/angel?branch=master)
[![Documentation Status](https://readthedocs.org/projects/libangel/badge/?version=latest)](https://libangel.readthedocs.io/en/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# angel
<img src="https://github.com/fmozafari/angel/blob/master/angel.svg" width="64" height="64" align="left" style="margin-right: 12pt" />
angel is a C++-17 Quantom State Preparation (QSP) library. It provides several algorithms to enable a scalable QSP and reduce the number of CNOTs.

Read the full documentation [here](https://libangel.readthedocs.io/en/latest/index.html).

## Example

The following code shows the uniform quantum state preparation for the GHZ(3) state. To prepare the state, variable reordering and dependency analysis methods are utilized. The number of CNOTs and the number of single-qubit gates are reported. 

```c++
#include <angel/dependency_analysis/esop_based_dependency_analysis.hpp>
#include <angel/quantum_state_preparation/qsp_deps.hpp>
#include <angel/reordering/no_reordering.hpp>
#include <tweedledum/IR/Circuit.h>
#include <tweedledum/IR/Instruction.h>
#include <tweedledum/Utils/Visualization/string_utf8.h>
#include <kitty/constructors.hpp>

/* representing uniform quantum state as a truth table */
kitty::dynamic_truth_table tt( 3 );
kitty::create_from_binary_string( tt, "10000001" );

/* reordering strategy */
angel::no_reordering no_reorder;

/* dependency analysis method */
angel::esop_deps_analysis::parameter_type esop_ps;
angel::esop_deps_analysis::statistics_type esop_st;
angel::esop_deps_analysis esop( esop_ps, esop_st );

/* initialize the uniform quantum state preparation method */
angel::state_preparation_parameters qsp_ps;
angel::state_preparation_statistics qsp_st;
tweedledum::Circuit network;




Note that angel does not work on windows currently.
