set(LIB Qui)
find_package(Qt5 COMPONENTS Core Gui Widgets Sql Xml OpenGL REQUIRED)

set( HEADERS
   AdcTab.h
   AimdTab.h
   AttenuationParameterTab.h
   AuxiliaryBasisTab.h
   CisTab.h
   EomTab.h
   FreezingStringTab.h
   FrequenciesTab.h
   GeometryConstraint.h
   InputDialog.h
   OptionDatabaseForm.h
   OptionEditors.h
   OptionEditors.h
   PrimaryBasisTab.h
   PropertiesTab.h
   QtNode.h
   QuiMolecule.h
   ReactionPathTab.h
   TransitionStateTab.h
)

set( SOURCES
   Actions.C
   ExternalChargesSection.C
   GeometryConstraint.C
   InputDialog.C
   InputDialogLogic.C
   KeyValueSection.C
   KeywordSection.C
   LJParametersSection.C
   MoleculeSection.C
   OptSection.C
   Option.C
   OptionDatabase.C
   OptionDatabaseForm.C
   OptionEditors.C
   PcmSection.C
   Qui.C
   QuiJob.C
   QuiMolecule.C
   ReadInput.C
   RemSection.C
)

set( UI_FILES
   AdcTab.ui
   AimdTab.ui
   AttenuationParameterTab.ui
   AuxiliaryBasisTab.ui
   CisTab.ui
   EomTab.ui
   FreezingStringTab.ui
   FrequenciesTab.ui
   GeometryConstraintDialog.ui
   OptionDatabaseForm.ui
   OptionListEditor.ui
   OptionNumberEditor.ui
   PrimaryBasisTab.ui
   PropertiesTab.ui
   QuiMainWindow.ui
   ReactionPathTab.ui
   TransitionStateTab.ui
)

qt5_wrap_ui( UI_HEADERS ${UI_FILES} )
qt5_wrap_cpp(SOURCES ${HEADERS} )
add_library(${LIB} ${SOURCES} ${UI_HEADERS})
target_include_directories(${LIB} PUBLIC
   "${${LIB}_SOURCE_DIR}" "${CMAKE_CURRENT_BINARY_DIR}"
   "${OpenBabel3_INCLUDE_DIRS}"
)
target_link_libraries(${LIB} PUBLIC
   Process
)
target_link_libraries(${LIB} PRIVATE
   Data
   Parser
   Util
   Qt5::Core
   Qt5::Gui
   Qt5::Widgets
   Qt5::Xml
   Qt5::Sql
   Qt5::OpenGL
   ${OpenBabel3_LIBRARIES}
)

