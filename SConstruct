import os
import sys
import gslab_scons
gslab_scons.start_log() 

env = Environment(ENV = {'PATH' : os.environ['PATH']}, 
                  IMPLICIT_COMMAND_DEPENDENCIES = 0,
                  BUILDERS = { #'Tablefill' : Builder(action = build.build_tables),
                              'Lyx'       : Builder(action = gslab_scons.build_lyx),
                               #'R'         : Builder(action = build.build_r),
                              'Stata'  : Builder(action = gslab_scons.build_stata),
                              'Python' : Builder(action = gslab_scons.build_python),
                              'Matlab' : Builder(action = gslab_scons.build_matlab)},
                  user_flavor = ARGUMENTS.get('sf', 'StataSE-64'))


env.Decider('MD5-timestamp') # Only computes hash if time-stamp changed
Export('env')

SConscript('source/data/SConscript') 
SConscript('source/analysis/SConscript')
SConscript('source/paper/SConscript') 
SConscript('source/talk/SConscript')