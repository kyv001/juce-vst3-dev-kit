# juce-vst3-dev-kit
JUCE VST3 Plugin Development Kit

## Using
1. Add this repo in your project as submodule.  
```shell
git submodule add https://github.com/Do-sth-sharp/juce-vst3-dev-kit.git
```

2. Set plugin information variables in your CMakeLists.txt  
```cmake
set (DMDA_ENABLED ON)#As you need
set (JucePlugin_Name "Your Plugin Name")
set (JucePlugin_Desc "Your Plugin Description")
set (JucePlugin_Manufacturer "Manufacturer Name")
set (JucePlugin_ManufacturerWebsite "https://web.site")
set (JucePlugin_ManufacturerEmail "e-mail@mail.com")
set (JucePlugin_Version "0.0.0")
set (JucePlugin_VersionCode "0x000000")
set (JucePlugin_ManufacturerCode "0xabcdef00")
set (JucePlugin_PluginCode "0xabcdefff")
set (JucePlugin_IsSynth TRUE)
set (JucePlugin_IsMidiEffect FALSE)
set (JucePlugin_WantsMidiInput TRUE)
set (JucePlugin_ProducesMidiOutput FALSE)
set (JucePlugin_EditorRequiresKeyboardFocus TRUE)
set (JucePlugin_Vst3Category "Instrument|Generator|Synth")
set (JucePlugin_CFBundleIdentifier "com.organ.project.plugin")
set (JucePlugin_VSTNumMidiInputs "16")
set (JucePlugin_VSTNumMidiOutputs "0")
set (JucePlugin_MaxNumInputChannels "0")
set (JucePlugin_MaxNumOutputChannels "1")
set (JucePlugin_PreferredChannelConfigurations "{0, 1}")
```

3. Add sub directory into your CMakeLists.txt  
```cmake
add_subdirectory (juce-vst3-dev-kit)
```

4. Link libJUCE to your target.  
```cmake
target_link_libraries (targetName PRIVATE libJUCE ...)
```