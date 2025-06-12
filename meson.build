project('pentacle', 'cpp', 'c')

srcs = ['src/main.cpp']

glfw_lib = dependency('glfw3', required: true)
imgui_lib = dependency('imgui', required: true)

if not glfw_lib.found()
  glfw_proj = subproject('glfw3')
  glfw_lib = glfw_proj.get_variable('glfw3')
endif

  imgui_compiled_options = ['opengl=true','glfw=true','dx9=false', 'dx10=false', 'dx11=false', 'dx12=false']

if not imgui_lib.found()
  imgui_proj = subproject('imgui', default_options: imgui_compiled_options)
  imgui_lib = imgui_proj.get_variable('imgui')
endif

deps = [glfw_lib, imgui_lib]

executable('pentacle', sources: srcs, dependencies: deps)
