project('pentacle', 'cpp', 'c')

incdir = include_directories('deps')
glad_sources = files('deps/glad/glad.c')
srcs = ['src/main.cpp', glad_sources]

glfw_lib = dependency('glfw3', required: true)
imgui_lib = dependency('imgui', required: true)

if not glfw_lib.found()
  glfw_proj = subproject('glfw3')
  glfw_lib = glfw_proj.get_variable('glfw3')
endif

deps = [glfw_lib, imgui_lib]

executable('pentacle', sources: srcs, dependencies: deps, include_directories: incdir)
