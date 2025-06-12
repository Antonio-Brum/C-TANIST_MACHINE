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

if not imgui_lib.found()
  imgui_proj = subproject('imgui')
  imgui_lib = imgui_proj.get_variable('imgui')
endif

deps = [glfw_lib, imgui_lib]

opengl_dep = dependency('gl', required: false)
if not opengl_dep.found()
  if host_machine.system() == 'windows'
    opengl_dep = dependency('opengl32', required: false)
    if not opengl_dep.found()
      opengl_dep = find_library('opengl32', required: true)
    endif
  else
    opengl_dep = find_library('GL', required: true)
  endif
endif
deps += [opengl_dep]

if host_machine.system() == 'windows'
  gdi32_dep = find_library('gdi32', required: false)
  user32_dep = find_library('user32', required: false)
  if gdi32_dep.found()
    deps += [gdi32_dep]
  endif
  if user32_dep.found()
    deps += [user32_dep]
  endif
endif

executable('pentacle', sources: srcs, dependencies: deps, include_directories: incdir)
