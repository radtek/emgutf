# --------------------------------------------------------
#  Copyright (C) 2004-2020 by EMGU Corporation. All rights reserved.
# --------------------------------------------------------

IF ( HAVE_IOS_LITE )

PROJECT(Emgu.TF.Lite.runtime.ios.nuget)
IF(WIN32)
ADD_CUSTOM_TARGET(
   ${PROJECT_NAME} ALL
   COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/../../../miscellaneous/nuget.exe" pack Package.nuspec -OutputDirectory "${CMAKE_CURRENT_SOURCE_DIR}/../"
)
ELSE()
ADD_CUSTOM_TARGET(
   ${PROJECT_NAME} ALL
   COMMAND mono "${CMAKE_CURRENT_SOURCE_DIR}/../../../miscellaneous/nuget.exe" pack Package.nuspec -OutputDirectory "${CMAKE_CURRENT_SOURCE_DIR}/../"
)
ENDIF()
ADD_DEPENDENCIES(${PROJECT_NAME} Emgu.TF.Lite.nuget)
IF(TARGET Emgu.TF.Lite.Runtime.iOS)
  ADD_DEPENDENCIES(${PROJECT_NAME} Emgu.TF.Lite.Runtime.iOS)
ENDIF()

if(ENABLE_SOLUTION_FOLDERS)
  set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER "NUGET")
endif() 

ENDIF()
