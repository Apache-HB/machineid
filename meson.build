project('machineid', ['cpp'],
    default_options : [
        'cpp_std=c++11',
        'cpp_eh=none'
    ],
    version : '1.0',
    license : 'GPL'
)

sources = 'src/machineid/machineid.cpp'
headers = 'include/machineid/machineid.h'

incdir = include_directories('include')

args = []

if meson.get_compiler('cpp').get_id() == 'msvc'
    args += '/EHsc-'
endif

machid_lib = static_library('machineid', sources, cpp_args : args, install : true)
machid_dep = declare_dependency(
    link_with : machid_lib,
    include_directories : incdir
)

pkg_mod = import('pkgconfig')
pkg_mod.generate(machid_lib,
    version : '1.0',
    name : 'machineid',
    filebase : 'machineid',
    description : 'C++ library to get unique machine id.'
)