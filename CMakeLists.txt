cmake_minimum_required(VERSION 3.22)

project(swift-hello LANGUAGES Swift)

add_executable(swift-hello
  Sources/swift-hello/main.swift)
target_compile_options(swift-hello PRIVATE
  -parse-as-library)
