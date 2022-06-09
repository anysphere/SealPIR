cc_library(
  name="sealpir",
  hdrs=["pir.hpp","pir_server.hpp","pir_client.hpp"],
  srcs=["pir.cpp","pir_server.cpp","pir_client.cpp"],
  linkstatic = True,
  deps=["@seal"]
)

cc_binary(
  name="main",
  srcs = ["main.cpp"],
  linkstatic=True,
  deps = [":sealpir"]
)