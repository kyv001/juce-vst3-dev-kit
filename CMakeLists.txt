cmake_minimum_required (VERSION 3.22)
project (juce-vst3-dev-kit VERSION 1.0.0 LANGUAGES C CXX)

if (NOT DEFINED CMAKE_BUILD_TYPE)
	set (CMAKE_BUILD_TYPE "Release"  CACHE STRING "Choose the type of build." FORCE)
endif (NOT DEFINED CMAKE_BUILD_TYPE)

set(CMAKE_CXX_STANDARD 20)# Using C++20
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_C_STANDARD 17)# Using C17
set(CMAKE_C_EXTENSIONS OFF)
set(CMAKE_C_STANDARD_REQUIRED ON)

set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>DLL")# Using /MD and /MDd on MSVC
if (MSVC)
	add_compile_definitions ("_CRT_SECURE_NO_WARNINGS")
endif (MSVC)

# ============================
# SDK Path
# ============================
set (JUCE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/JUCE")
set (JUCE_HEADER_PATH "${CMAKE_CURRENT_SOURCE_DIR}/JuceLibraryCode")
set (VST2_SDK_PATH "${CMAKE_CURRENT_SOURCE_DIR}/vst2-sdk-for-vst3sdk")
set (VST3_SDK_PATH "${CMAKE_CURRENT_SOURCE_DIR}/vst3sdk")
set (ARA_SDK_PATH "${CMAKE_CURRENT_SOURCE_DIR}/ARA_SDK")
set (ARA_EXTENSION_PATH "${CMAKE_CURRENT_SOURCE_DIR}/ARAExtension")

# ============================
# Options
# ============================
#set (JUCE_DISPLAY_SPLASH_SCREEN OFF)
#set (JUCE_USE_DARK_SPLASH_SCREEN ON)
set (JucePlugin_Build_VST OFF)
set (JucePlugin_Build_VST3 ON)
set (JucePlugin_Build_AU OFF)
set (JucePlugin_Build_AUv3 OFF)
set (JucePlugin_Build_LV2 OFF)
set (JucePlugin_Build_RTAS OFF)
set (JucePlugin_Build_AAX OFF)
set (JucePlugin_Build_Standalone OFF)
set (JucePlugin_Build_Unity OFF)
set (JUCE_USE_WINRT_MIDI OFF)
set (JUCE_ASIO OFF)
set (JUCE_JACK OFF)
set (JUCE_BELA OFF)
set (JUCE_USE_ANDROID_OPENSLES OFF)
set (JUCE_ASIO_DEBUGGING OFF)
set (JUCE_WINRT_MIDI_LOGGING OFF)
set (JUCE_CUSTOM_VST3_SDK ON)
set (JUCE_VST3_CAN_REPLACE_VST2 ON)
set (JUCE_USE_MP3AUDIOFORMAT OFF)
set (JUCE_USE_LAME_AUDIO_FORMAT OFF)

# ============================
# Default Options
# ============================
#if (NOT DEFINED JUCE_DISPLAY_SPLASH_SCREEN)
#	set (JUCE_DISPLAY_SPLASH_SCREEN OFF)
#endif (NOT DEFINED JUCE_DISPLAY_SPLASH_SCREEN)
#if (NOT DEFINED JUCE_USE_DARK_SPLASH_SCREEN)
#	set (JUCE_USE_DARK_SPLASH_SCREEN ON)
#endif (NOT DEFINED JUCE_USE_DARK_SPLASH_SCREEN)
if (NOT DEFINED JucePlugin_Build_VST)
	set (JucePlugin_Build_VST OFF)
endif (NOT DEFINED JucePlugin_Build_VST)
if (NOT DEFINED JucePlugin_Build_VST3)
	set (JucePlugin_Build_VST3 OFF)
endif (NOT DEFINED JucePlugin_Build_VST3)
if (NOT DEFINED JucePlugin_Build_AU)
	set (JucePlugin_Build_AU OFF)
endif (NOT DEFINED JucePlugin_Build_AU)
if (NOT DEFINED JucePlugin_Build_AUv3)
	set (JucePlugin_Build_AUv3 OFF)
endif (NOT DEFINED JucePlugin_Build_AUv3)
if (NOT DEFINED JucePlugin_Build_RTAS)
	set (JucePlugin_Build_RTAS OFF)
endif (NOT DEFINED JucePlugin_Build_RTAS)
if (NOT DEFINED JucePlugin_Build_AAX)
	set (JucePlugin_Build_AAX OFF)
endif (NOT DEFINED JucePlugin_Build_AAX)
if (NOT DEFINED JucePlugin_Build_Standalone)
	set (JucePlugin_Build_Standalone OFF)
endif (NOT DEFINED JucePlugin_Build_Standalone)
if (NOT DEFINED JucePlugin_Build_Unity)
	set (JucePlugin_Build_Unity OFF)
endif (NOT DEFINED JucePlugin_Build_Unity)
if (NOT DEFINED JucePlugin_Enable_ARA)
	set (JucePlugin_Enable_ARA OFF)
endif (NOT DEFINED JucePlugin_Enable_ARA)
if (NOT DEFINED JUCE_USE_WINRT_MIDI)
	set (JUCE_USE_WINRT_MIDI OFF)
endif (NOT DEFINED JUCE_USE_WINRT_MIDI)
if (NOT DEFINED JUCE_ASIO)
	set (JUCE_ASIO OFF)
endif (NOT DEFINED JUCE_ASIO)
if (NOT DEFINED JUCE_JACK)
	set (JUCE_JACK OFF)
endif (NOT DEFINED JUCE_JACK)
if (NOT DEFINED JUCE_BELA)
	set (JUCE_BELA OFF)
endif (NOT DEFINED JUCE_BELA)
if (NOT DEFINED JUCE_USE_ANDROID_OPENSLES)
	set (JUCE_USE_ANDROID_OPENSLES OFF)
endif (NOT DEFINED JUCE_USE_ANDROID_OPENSLES)
if (NOT DEFINED JUCE_ASIO_DEBUGGING)
	set (JUCE_ASIO_DEBUGGING OFF)
endif (NOT DEFINED JUCE_ASIO_DEBUGGING)
if (NOT DEFINED JUCE_WINRT_MIDI_LOGGING)
	set (JUCE_WINRT_MIDI_LOGGING OFF)
endif (NOT DEFINED JUCE_WINRT_MIDI_LOGGING)
if (NOT DEFINED JUCE_PLUGINHOST_VST)
	set (JUCE_PLUGINHOST_VST OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_VST)
if (NOT DEFINED JUCE_PLUGINHOST_VST3)
	set (JUCE_PLUGINHOST_VST3 OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_VST3)
if (NOT DEFINED JUCE_PLUGINHOST_AU)
	set (JUCE_PLUGINHOST_AU OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_AU)
if (NOT DEFINED JUCE_PLUGINHOST_LADSPA)
	set (JUCE_PLUGINHOST_LADSPA OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_LADSPA)
if (NOT DEFINED JUCE_PLUGINHOST_LV2)
	set (JUCE_PLUGINHOST_LV2 OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_LV2)
if (NOT DEFINED JUCE_PLUGINHOST_ARA)
	set (JUCE_PLUGINHOST_ARA OFF)
endif (NOT DEFINED JUCE_PLUGINHOST_ARA)
if (NOT DEFINED JUCE_CUSTOM_VST3_SDK)
	set (JUCE_CUSTOM_VST3_SDK OFF)
endif (NOT DEFINED JUCE_CUSTOM_VST3_SDK)
if (NOT DEFINED JUCE_USE_MP3AUDIOFORMAT)
	set (JUCE_USE_MP3AUDIOFORMAT OFF)
endif (NOT DEFINED JUCE_USE_MP3AUDIOFORMAT)
if (NOT DEFINED JUCE_USE_LAME_AUDIO_FORMAT)
	set (JUCE_USE_LAME_AUDIO_FORMAT OFF)
endif (NOT DEFINED JUCE_USE_LAME_AUDIO_FORMAT)

# ============================
# Module Path
# ============================
set (JUCE_INC_PATH "${JUCE_PATH}/modules")
if (UNIX AND NOT APPLE)
	find_package (PkgConfig REQUIRED)
	pkg_search_module (ALSA REQUIRED alsa)
	pkg_search_module (FREETYPE2 REQUIRED freetype2)
	pkg_search_module (LIBCURL REQUIRED libcurl)
	pkg_search_module (WEBKIT2GTK-4.0 REQUIRED webkit2gtk-4.0)
	pkg_search_module (GTK+-X11-3.0 REQUIRED gtk+-x11-3.0)

	set (JUCE_INC_LIST
		${ALSA_INCLUDE_DIRS}
		${FREETYPE2_INCLUDE_DIRS}
		${LIBCURL_INCLUDE_DIRS}
		${WEBKIT2GTK-4.0_INCLUDE_DIRS}
		${GTK+-X11-3.0_INCLUDE_DIRS}
	)

	find_library (RT rt)
	find_library (DL dl)
	find_library (PTHREAD pthread)
	find_library (GL GL)
endif (UNIX AND NOT APPLE)

if (JUCE_ASIO)
	if (DEFINED ASIO_SDK_PATH)
		set (JUCE_ASIO_INC_PATH ${ASIO_SDK_PATH})
	else (DEFINED ASIO_SDK_PATH)
		message (SEND_ERROR "ASIO SDK notfound!")
	endif (DEFINED ASIO_SDK_PATH)
endif (JUCE_ASIO)
if (JucePlugin_Build_VST OR ((JUCE_PLUGINHOST_VST3 OR JucePlugin_Build_VST3) AND JUCE_VST3_CAN_REPLACE_VST2))
	if (DEFINED VST2_SDK_PATH)
		set (JUCE_VST_INC_PATH ${VST2_SDK_PATH})
	else (DEFINED VST2_SDK_PATH)
		message (SEND_ERROR "VST SDK notfound!")
	endif (DEFINED VST2_SDK_PATH)
endif (JucePlugin_Build_VST OR ((JUCE_PLUGINHOST_VST3 OR JucePlugin_Build_VST3) AND JUCE_VST3_CAN_REPLACE_VST2))
if (JucePlugin_Build_VST3 AND JUCE_CUSTOM_VST3_SDK)
	if (DEFINED VST3_SDK_PATH)
		set (JUCE_VST3_INC_PATH ${VST3_SDK_PATH})
	else (DEFINED VST3_SDK_PATH)
		message (SEND_ERROR "VST3 SDK notfound!")
	endif (DEFINED VST3_SDK_PATH)
endif (JucePlugin_Build_VST3 AND JUCE_CUSTOM_VST3_SDK)
if (JucePlugin_Build_LV2)
	#LV2 SDK Path
	set (JUCE_LV2_INC_PATH
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/lv2"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/lilv"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/lilv/src"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/serd"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/sord"
		"${CMAKE_CURRENT_SOURCE_DIR}/JUCE/modules/juce_audio_processors/format_types/LV2_SDK/sratom"
		)

	#LV2 SDK Src
	set (JUCE_LV2_SRC_FIX
		"${JUCE_HEADER_PATH}/include_juce_audio_processors_lv2_libs.cpp"
	)
endif (JucePlugin_Build_LV2)
if (JucePlugin_Enable_ARA)
	if (DEFINED ARA_SDK_PATH)
		set (JUCE_ARA_INC_PATH ${ARA_SDK_PATH} ${ARA_EXTENSION_PATH})
	else (DEFINED ARA_SDK_PATH)
		message (SEND_ERROR "ARA SDK notfound!")
	endif (DEFINED ARA_SDK_PATH)

	#ARA SDK Src
	if (JucePlugin_Enable_ARA)
	set (JUCE_ARA_SRC_FIX
		"${ARA_SDK_PATH}/ARA_Library/PlugIn/ARAPlug.cpp"
		"${JUCE_HEADER_PATH}/include_juce_audio_processors_ara.cpp"
		"${ARA_SDK_PATH}/ARA_Library/Dispatch/ARAPlugInDispatch.cpp"
		"${ARA_SDK_PATH}/ARA_Library/Utilities/ARAChannelFormat.cpp"
	)
	endif (JucePlugin_Enable_ARA)
endif (JucePlugin_Enable_ARA)

set (JUCE_PUBLIC_INC_PATH
	${JUCE_HEADER_PATH}
	${JUCE_INC_PATH}
	${JUCE_ARA_INC_PATH}
	${JUCE_ASIO_INC_PATH}
	${JUCE_VST_INC_PATH}
	${JUCE_VST3_INC_PATH}
	${JUCE_LV2_INC_PATH}
)
set (JUCE_PRIVATE_INC_PATH
	${JUCE_INC_LIST}
)

# ============================
# Target
# ============================
set (JUCE_AUDIO_SRC
		"${JUCE_HEADER_PATH}/include_juce_audio_basics.cpp"
		"${JUCE_HEADER_PATH}/include_juce_audio_devices.cpp"
		"${JUCE_HEADER_PATH}/include_juce_audio_formats.cpp"
		"${JUCE_HEADER_PATH}/include_juce_audio_processors.cpp"
		"${JUCE_HEADER_PATH}/include_juce_audio_utils.cpp"
)
set (JUCE_CORE_SRC
		"${JUCE_HEADER_PATH}/include_juce_core.cpp"
		"${JUCE_HEADER_PATH}/include_juce_core_CompilationTime.cpp"
		"${JUCE_HEADER_PATH}/include_juce_cryptography.cpp"
		"${JUCE_HEADER_PATH}/include_juce_gui_basics.cpp"
		"${JUCE_HEADER_PATH}/include_juce_gui_extra.cpp"
		"${JUCE_HEADER_PATH}/include_juce_events.cpp"
		"${JUCE_HEADER_PATH}/include_juce_data_structures.cpp"
		"${JUCE_HEADER_PATH}/include_juce_graphics.cpp"
		"${JUCE_HEADER_PATH}/include_juce_graphics_Harfbuzz.cpp"
		"${JUCE_HEADER_PATH}/include_juce_graphics_Sheenbidi.c"
		"${JUCE_HEADER_PATH}/include_juce_osc.cpp"
		"${JUCE_HEADER_PATH}/include_juce_box2d.cpp"
		"${JUCE_HEADER_PATH}/include_juce_opengl.cpp"
		"${JUCE_HEADER_PATH}/include_juce_analytics.cpp"
		"${JUCE_HEADER_PATH}/include_juce_product_unlocking.cpp"
		"${JUCE_HEADER_PATH}/include_juce_video.cpp"
		"${JUCE_HEADER_PATH}/include_juce_animation.cpp"
)
set (JUCE_DSP_SRC
		"${JUCE_HEADER_PATH}/include_juce_dsp.cpp"
)
set (JUCE_VST3_SRC
		"${JUCE_HEADER_PATH}/include_juce_audio_plugin_client_VST3.cpp"
)

set (JUCE_SRC
	${JUCE_AUDIO_SRC} ${JUCE_CORE_SRC} ${JUCE_DSP_SRC} ${JUCE_VST3_SRC}
	"${JUCE_HEADER_PATH}/JuceHeader.h")
add_library (juce STATIC ${JUCE_SRC} ${JUCE_LV2_SRC_FIX} ${JUCE_ARA_SRC_FIX})
set_source_files_properties ("${JUCE_HEADER_PATH}/JuceHeader.h" PROPERTIES HEADER_FILE_ONLY TRUE)

foreach (ITEM ${JUCE_PUBLIC_INC_PATH})
	file (RELATIVE_PATH ITEM_PATH ${CMAKE_CURRENT_SOURCE_DIR} ${ITEM})
	target_include_directories (juce PUBLIC
		"${CMAKE_CURRENT_SOURCE_DIR}/${ITEM_PATH}"
	)
endforeach (ITEM ${JUCE_PUBLIC_INC_PATH})
foreach (ITEM ${JUCE_PRIVATE_INC_PATH})
	file (RELATIVE_PATH ITEM_PATH ${CMAKE_CURRENT_SOURCE_DIR} ${ITEM})
	target_include_directories (juce PRIVATE ${ITEM_PATH})
endforeach (ITEM ${JUCE_PRIVATE_INC_PATH})

# ============================
# Definitions
# ============================
set (JUCE_DEBUG_DEF "$<$<CONFIG:Debug>:DEBUG=1>" "$<$<CONFIG:Debug>:_DEBUG=1>" "$<$<NOT:$<CONFIG:Debug>>:NDEBUG=1>")
set (JUCE_NDEBUG_DEF "NDEBUG=1")
set (JUCE_LINUX_DEF "LINUX=1")
set (JUCE_WIN_DEF "")
set (JUCE_OSX_DEF "")

set (JUCE_MODULE_DEF 
	#"JUCE_DISPLAY_SPLASH_SCREEN=$<IF:$<BOOL:${JUCE_DISPLAY_SPLASH_SCREEN}>,1,0>"
	#"JUCE_USE_DARK_SPLASH_SCREEN=$<IF:$<BOOL:${JUCE_USE_DARK_SPLASH_SCREEN}>,1,0>"
	"JUCE_MODULE_AVAILABLE_juce_analytics=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_basics=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_devices=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_formats=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_plugin_client=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_processors=1"
	"JUCE_MODULE_AVAILABLE_juce_audio_utils=1"
	"JUCE_MODULE_AVAILABLE_juce_box2d=1"
	"JUCE_MODULE_AVAILABLE_juce_core=1"
	"JUCE_MODULE_AVAILABLE_juce_cryptography=1"
	"JUCE_MODULE_AVAILABLE_juce_data_structures=1"
	"JUCE_MODULE_AVAILABLE_juce_dsp=1"
	"JUCE_MODULE_AVAILABLE_juce_events=1"
	"JUCE_MODULE_AVAILABLE_juce_graphics=1"
	"JUCE_MODULE_AVAILABLE_juce_gui_basics=1"
	"JUCE_MODULE_AVAILABLE_juce_gui_extra=1"
	"JUCE_MODULE_AVAILABLE_juce_opengl=1"
	"JUCE_MODULE_AVAILABLE_juce_osc=1"
	"JUCE_MODULE_AVAILABLE_juce_product_unlocking=1"
	"JUCE_MODULE_AVAILABLE_juce_video=1"
	"JUCE_GLOBAL_MODULE_SETTINGS_INCLUDED=1"
	"JUCE_STRICT_REFCOUNTEDPOINTER=1"
	"JUCE_STANDALONE_APPLICATION=0"
	"DONT_SET_USING_JUCE_NAMESPACE=1"
	"JucePlugin_Build_VST=$<IF:$<BOOL:${JucePlugin_Build_VST}>,1,0>"
	"JucePlugin_Build_VST3=$<IF:$<BOOL:${JucePlugin_Build_VST3}>,1,0>"
	"JucePlugin_Build_AU=$<IF:$<BOOL:${JucePlugin_Build_AU}>,1,0>"
	"JucePlugin_Build_AUv3=$<IF:$<BOOL:${JucePlugin_Build_AUv3}>,1,0>"
	"JucePlugin_Build_LV2=$<IF:$<BOOL:${JucePlugin_Build_LV2}>,1,0>"
	"JucePlugin_Build_RTAS=$<IF:$<BOOL:${JucePlugin_Build_RTAS}>,1,0>"
	"JucePlugin_Build_AAX=$<IF:$<BOOL:${JucePlugin_Build_AAX}>,1,0>"
	"JucePlugin_Build_Standalone=$<IF:$<BOOL:${JucePlugin_Build_Standalone}>,1,0>"
	"JucePlugin_Build_Unity=$<IF:$<BOOL:${JucePlugin_Build_Unity}>,1,0>"
	"JUCE_USE_WINRT_MIDI=$<IF:$<BOOL:${JUCE_USE_WINRT_MIDI}>,1,0>"
	"JUCE_ASIO=$<IF:$<BOOL:${JUCE_ASIO}>,1,0>"
	"JUCE_JACK=$<IF:$<BOOL:${JUCE_JACK}>,1,0>"
	"JUCE_BELA=$<IF:$<BOOL:${JUCE_BELA}>,1,0>"
	"JUCE_USE_ANDROID_OPENSLES=$<IF:$<BOOL:${JUCE_USE_ANDROID_OPENSLES}>,1,0>"
	"JUCE_ASIO_DEBUGGING=$<IF:$<BOOL:${JUCE_ASIO_DEBUGGING}>,1,0>"
	"JUCE_WINRT_MIDI_LOGGING=$<IF:$<BOOL:${JUCE_WINRT_MIDI_LOGGING}>,1,0>"
	"JUCE_CUSTOM_VST3_SDK=$<IF:$<BOOL:${JUCE_CUSTOM_VST3_SDK}>,1,0>"
	"JUCE_VST3_CAN_REPLACE_VST2=$<IF:$<BOOL:${JUCE_VST3_CAN_REPLACE_VST2}>,1,0>"
	"JUCE_USE_MP3AUDIOFORMAT=$<IF:$<BOOL:${JUCE_USE_MP3AUDIOFORMAT}>,1,0>"
	"JUCE_USE_LAME_AUDIO_FORMAT=$<IF:$<BOOL:${JUCE_USE_LAME_AUDIO_FORMAT}>,1,0>"
	"JucePlugin_Enable_ARA=$<IF:$<BOOL:${JucePlugin_Enable_ARA}>,1,0>"
)

set (JUCE_PLUGIN_DEF
	"JucePlugin_Name=\"${JucePlugin_Name}\""
	"JucePlugin_Desc=\"${JucePlugin_Desc}\""
	"JucePlugin_Manufacturer=\"${JucePlugin_Manufacturer}\""
	"JucePlugin_ManufacturerWebsite=\"${JucePlugin_ManufacturerWebsite}\""
	"JucePlugin_ManufacturerEmail=\"${JucePlugin_ManufacturerEmail}\""
	"JucePlugin_Version=${JucePlugin_Version}"
	"JucePlugin_VersionCode=${JucePlugin_VersionCode}"
	"JucePlugin_VersionString=\"${JucePlugin_Version}\""
	"JucePlugin_ManufacturerCode=${JucePlugin_ManufacturerCode}"
	"JucePlugin_PluginCode=${JucePlugin_PluginCode}"
	"JucePlugin_IsSynth=$<IF:$<BOOL:${JucePlugin_IsSynth}>,1,0>"
	"JucePlugin_IsMidiEffect=$<IF:$<BOOL:${JucePlugin_IsMidiEffect}>,1,0>"
	"JucePlugin_WantsMidiInput=$<IF:$<BOOL:${JucePlugin_WantsMidiInput}>,1,0>"
	"JucePlugin_ProducesMidiOutput=$<IF:$<BOOL:${JucePlugin_ProducesMidiOutput}>,1,0>"
	"JucePlugin_EditorRequiresKeyboardFocus=$<IF:$<BOOL:${JucePlugin_EditorRequiresKeyboardFocus}>,1,0>"
	"JucePlugin_VSTUniqueID=${JucePlugin_PluginCode}"
	"JucePlugin_Vst3Category=\"${JucePlugin_Vst3Category}\""
	"JucePlugin_CFBundleIdentifier=${JucePlugin_CFBundleIdentifier}"
	"JucePlugin_VSTNumMidiInputs=${JucePlugin_VSTNumMidiInputs}"
	"JucePlugin_VSTNumMidiOutputs=${JucePlugin_VSTNumMidiOutputs}"
	"JucePlugin_MaxNumInputChannels=${JucePlugin_MaxNumInputChannels}"
	"JucePlugin_MaxNumOutputChannels=${JucePlugin_MaxNumOutputChannels}"
	"JucePlugin_PreferredChannelConfigurations=${JucePlugin_PreferredChannelConfigurations}"
	"JucePlugin_ARACompatibleArchiveIDs=\"${JucePlugin_ARACompatibleArchiveIDs}\""
	"JucePlugin_ARAContentTypes=${JucePlugin_ARAContentTypes}"
	"JucePlugin_ARATransformationFlags=${JucePlugin_ARATransformationFlags}"
	"JucePlugin_ARAFactoryID=\"${JucePlugin_ARAFactoryID}\""
	"JucePlugin_ARADocumentArchiveID=\"${JucePlugin_ARADocumentArchiveID}\""
)

target_compile_definitions (juce PUBLIC ${JUCE_DEBUG_DEF})

if (WIN32)
	target_compile_definitions (juce PUBLIC ${JUCE_WIN_DEF})
elseif (UNIX AND NOT APPLE)
	target_compile_definitions (juce PUBLIC ${JUCE_LINUX_DEF})
elseif (APPLE)
	target_compile_definitions (juce PUBLIC ${JUCE_OSX_DEF})
endif ()

target_compile_definitions (juce PUBLIC ${JUCE_MODULE_DEF} ${JUCE_PLUGIN_DEF})

if (GNU OR MINGW)
	target_compile_definitions (juce PUBLIC "JUCE_USE_DIRECTWRITE=0")
endif (GNU OR MINGW)

target_compile_definitions (juce PUBLIC "JUCE_MODAL_LOOPS_PERMITTED=1" "JUCE_CATCH_UNHANDLED_EXCEPTIONS=1")

if (JUCE_DISABLE_LEAK_DETECTOR)
	target_compile_definitions (juce PUBLIC "JUCE_CHECK_MEMORY_LEAKS=0")
endif (JUCE_DISABLE_LEAK_DETECTOR)


# ============================
# Compile Options
# ============================
if (NOT MSVC)
	target_compile_options (juce PRIVATE
			-pthread
			-fvisibility=hidden
			-fvisibility-inlines-hidden
			"-Wa,-mbig-obj"
	)
	if (NOT (("${CMAKE_CXX_COMPILER_ID}" MATCHES "Clang") AND WIN32))
		target_compile_options (juce PRIVATE -fPIC)
	endif ()
	target_link_options (juce PRIVATE
			-shared
			-fvisibility=hidden
			-fvisibility-inlines-hidden
	)

	if (WIN32)
		target_link_libraries (juce PRIVATE
			-m64
			-lcomctl32
			-lwinmm
			-lwsock32
			-lwininet
			-lversion
			-lws2_32
			-loleaut32
			-limm32
			-lshlwapi
			-lrpcrt4
			-lopengl32
			-ldxgi
		)
		if (NOT ("${CMAKE_CXX_COMPILER_ID}" MATCHES "Clang"))
			target_link_libraries (juce PRIVATE -s)
		endif ()
	elseif (UNIX AND NOT APPLE)
		target_link_libraries (juce PRIVATE
			${RT}
			${DL}
			${PTHREAD}
			${GL}
			${ALSA_LIBRARIES}
			${FREETYPE2_LIBRARIES}
			${LIBCURL_LIBRARIES}
		)
	elseif (APPLE)
		target_link_libraries (juce PRIVATE
			"-framework Accelerate"
			"-framework AudioToolbox"
			"-framework AVFoundation"
			"-framework AVKit"
			"-framework Carbon"
			"-framework Cocoa"
			"-framework CoreAudio"
			"-framework CoreAudioKit"
			"-framework CoreMedia"
			"-framework CoreMIDI"
			"-framework DiscRecording"
			"-framework Foundation"
			"-framework IOKit"
			"-framework OpenGL"
			"-framework QuartzCore"
			"-framework WebKit"
		)
	endif ()
else (NOT MSVC)
	target_link_options (juce PUBLIC
		/INCLUDE:GetPluginFactory
	)

	if (CMAKE_BUILD_TYPE STREQUAL Debug)
		target_compile_options (juce PRIVATE
			/permissive-#符合模式:是
			/GS#安全检查:启用安全检查
			/Zc:wchar_t#将WChar_t视为内置类型:是
			/Gm-#启用最小重新生成:否
			/sdl-#SDL检查:否
			/fp:precise#浮点模型:精度
			/Zc:forScope#强制For循环范围中的合规性:是
			/Gd#调用约定:__cdecl
			/nologo#取消显示启动版权标志:是
			/bigobj#较大生成对象:是
		)
		target_link_options (juce PRIVATE
			/MANIFEST#生成清单:是
			/NXCOMPAT#数据执行保护(DEP):是
			/DYNAMICBASE#随机基址:是
			/LARGEADDRESSAWARE#启用大地址:是
			/SUBSYSTEM:WINDOWS#子系统:窗口
			/MANIFESTUAC:NO#启用用户账户控制:否
			/NOLOGO#取消显示启动版权标志:是
		)
	else (CMAKE_BUILD_TYPE STREQUAL Debug)
		target_compile_options (juce PRIVATE
			/permissive-#符合模式:是
			/GS#安全检查:启用安全检查
			/GL#全程序优化:是
			/Gy#启用函数级链接:是
			/Zc:wchar_t#将WChar_t视为内置类型:是
			/Gm-#启用最小重新生成:否
			/sdl-#SDL检查:否
			/fp:precise#浮点模型:精度
			/Zc:forScope#强制For循环范围中的合规性:是
			/Gd#调用约定:__cdecl
			/Oi#启用内部函数:是
			/nologo#取消显示启动版权标志:是
			/bigobj#较大生成对象:是
		)
		target_link_options (juce PRIVATE
			/MANIFEST#生成清单:是
			/LTCG:incremental#链接时间代码生成:使用快速链接时间代码生成
			/NXCOMPAT#数据执行保护(DEP):是
			/DYNAMICBASE#随机基址:是
			/LARGEADDRESSAWARE#启用大地址:是
			/OPT:REF#引用:是
			/SUBSYSTEM:WINDOWS#子系统:窗口
			/MANIFESTUAC:NO#启用用户账户控制:否
			/OPT:ICF#启用COMDAT折叠:是
			/NOLOGO#取消显示启动版权标志:是
		)
	endif (CMAKE_BUILD_TYPE STREQUAL Debug)
endif (NOT MSVC)
