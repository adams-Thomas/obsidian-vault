##### Layer Based
Each step in the Dockerfile is classed as a layer. 
As each step or layer is executed, the result is cached. This then speeds up future builds for layers that do not change.