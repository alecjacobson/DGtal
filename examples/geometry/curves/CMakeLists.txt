add_subdirectory(estimation)

SET(DGTAL_EXAMPLES_SRC
  greedy-dss-decomposition
  greedyAlphaThickDecomposition
  convex-and-concave-parts
  exampleAlphaThickSegment
  exampleAlphaThickSegmentNoisy
  exampleAlphaThickSegmentTgtCover
  exampleGridCurve2d
  exampleStabbingLineComputer
  exampleStabbingCircleComputer
  exampleFrechetShortcut 
  exampleArithmeticalDSS
  exampleArithmeticalDSSComputer
  exampleDSLSubsegment
  exampleArithmeticalDSL
  exampleNaive3DDSSComputer
  exampleArithDSSIterator
)


FOREACH(FILE ${DGTAL_EXAMPLES_SRC})
  add_executable(${FILE} ${FILE})
  # The dependancy libs are needed
  target_link_libraries (${FILE} DGtal ${DGtalLibDependencies} )
ENDFOREACH(FILE)



IF(MAGICK++_FOUND)
  SET(DGTALE_EXAMPLES_IO_Magick
    freemanChainDisplay
    )
  FOREACH(FILE ${DGTALE_EXAMPLES_IO_Magick})
    add_executable(${FILE} ${FILE})
    # The dependancy libs are needed
    target_link_libraries (${FILE} DGtal ${DGtalLibDependencies} )
  ENDFOREACH(FILE)
ENDIF(MAGICK++_FOUND)


### Test with QGLViewer
if (  WITH_VISU3D_QGLVIEWER )
   SET(DGTAL_EXAMPLES_QGL_SRC
      exampleArithDSS3d
     exampleGridCurve3d
     exampleGridCurve3d-2
     exampleParamCurve3dDigitization
     exampleParamCurve3dDigitizationTransformationDecorator
     exampleTrofoliKnot
     )
 
  FOREACH(FILE ${DGTAL_EXAMPLES_QGL_SRC} ) 
   add_executable(${FILE} ${FILE})
    # The dependancy libs are needed
    target_link_libraries (${FILE} DGtal ${DGtalLibDependencies})
  ENDFOREACH(FILE)

endif ( WITH_VISU3D_QGLVIEWER   )

