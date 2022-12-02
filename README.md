# xsar

radarSat2 Level 1 python reader for efficient xarray/dask based processor



# Install


```
conda install -c conda-forge xradarsat2
```

```pycon
>>> import xradarsat2
>>> folder_path = "/level1/root/directory"
>>> xradarsat2.rs2_reader(folder_path)
DataTree('None', parent=None)
├── DataTree('orbitAndAttitude')
│       Dimensions:    (timeStamp: 7)
│       Coordinates:
│         * timeStamp  (timeStamp) datetime64[ns] 2010-10-15T21:01:32.370461 ... 2010...
│       Data variables:
│           yaw        (timeStamp) float64 3.756 3.773 3.785 3.792 3.807 3.82 3.83
│           roll       (timeStamp) float64 -29.8 -29.8 -29.8 -29.8 -29.8 -29.8 -29.8
│           pitch      (timeStamp) float64 0.002605 0.002862 ... -0.001594 -0.001443
│           xPosition  (timeStamp) float64 -5.072e+06 -5.076e+06 ... -5.087e+06
│           yPosition  (timeStamp) float64 4.643e+06 4.676e+06 ... 4.799e+06 4.828e+06
│           zPosition  (timeStamp) float64 2.033e+06 1.944e+06 ... 1.584e+06 1.494e+06
│           xVelocity  (timeStamp) float64 -425.7 -352.1 -278.6 ... -131.8 -58.51 14.65
│           yVelocity  (timeStamp) float64 2.642e+03 2.58e+03 ... 2.324e+03 2.259e+03
│           zVelocity  (timeStamp) float64 -7.063e+03 -7.09e+03 ... -7.207e+03
│       Attributes:
│           attitudeDataSource:      Downlink
│           attitudeOffsetsApplied:  true
│           Description:             Attitude Information Data Store. Orbit Informati...
├── DataTree('geolocationGrid')
│       Dimensions:    (line: 11, pixel: 11)
│       Coordinates:
│         * line       (line) int64 0 1007 2015 3023 4031 5039 6046 7054 8062 9070 10078
│         * pixel      (pixel) int64 0 1043 2086 3129 4172 ... 6258 7301 8344 9387 10431
│       Data variables:
│           latitude   (line, pixel) float64 17.97 17.89 17.8 ... 12.77 12.67 12.57
│           longitude  (line, pixel) float64 130.4 130.9 131.4 ... 133.3 133.8 134.3
│           height     (line, pixel) float64 0.0 0.0 0.0 0.0 0.0 ... 0.0 0.0 0.0 0.0 0.0
│       Attributes: (12/13)
│           productFormat:                               GeoTIFF
│           outputMediaInterleaving:                     BSQ
│           rasterAttributes_dataType:                   Magnitude Detected
│           rasterAttributes_bitsPerSample_dataStream:   Magnitude
│           rasterAttributes_bitsPerSample_value:        16
│           rasterAttributes_numberOfSamplesPerLine:     10432
│           ...                                          ...
│           rasterAttributes_sampledPixelSpacing_units:  m
│           rasterAttributes_sampledPixelSpacing_value:  50.0
│           rasterAttributes_sampledLineSpacing_units:   m
│           rasterAttributes_sampledLineSpacing_value:   50.0
│           rasterAttributes_lineTimeOrdering:           Increasing
│           rasterAttributes_pixelTimeOrdering:          Decreasing
├── DataTree('imageGenerationParameters')
│   ├── DataTree('doppler')
│   │   ├── DataTree('dopplerCentroid')
│   │   │       Dimensions:                          (timeOfDopplerCentroidEstimate: 5,
│   │   │                                             n-Coefficients: 5)
│   │   │       Coordinates:
│   │   │         * timeOfDopplerCentroidEstimate    (timeOfDopplerCentroidEstimate) datetime64[ns] ...
│   │   │         * n-Coefficients                   (n-Coefficients) int64 0 1 2 3 4
│   │   │       Data variables:
│   │   │           dopplerAmbiguity                 (timeOfDopplerCentroidEstimate) int64 0 ...
│   │   │           dopplerAmbiguityConfidence       (timeOfDopplerCentroidEstimate) float64 ...
│   │   │           dopplerCentroidReferenceTime     (timeOfDopplerCentroidEstimate) float64 ...
│   │   │           dopplerCentroidPolynomialPeriod  (timeOfDopplerCentroidEstimate) float64 ...
│   │   │           dopplerCentroidCoefficients      (timeOfDopplerCentroidEstimate, n-Coefficients) float64 ...
│   │   │           dopplerCentroidConfidence        (timeOfDopplerCentroidEstimate) float64 ...
│   │   │       Attributes:
│   │   │           Description:  Doppler Centroid Data Store
│   │   └── DataTree('dopplerRateValues')
│   │           Dimensions:                   (dopplerRateReferenceTime: 1,
│   │                                          n-RateValuesCoefficients: 3)
│   │           Coordinates:
│   │             * dopplerRateReferenceTime  (dopplerRateReferenceTime) float64 0.005568
│   │             * n-RateValuesCoefficients  (n-RateValuesCoefficients) int64 0 1 2
│   │           Data variables:
│   │               dopplerRateValues         (dopplerRateReferenceTime, n-RateValuesCoefficients) float64 ...
│   │           Attributes:
│   │               Description:  Doppler Rate Values Data Store.
│   └── DataTree('chirp')
│           Dimensions:                  (pole: 1, n-amplitudeCoefficients: 4,
│                                         n-phaseCoefficients: 4)
│           Coordinates:
│             * pole                     (pole) <U2 'VV'
│             * n-amplitudeCoefficients  (n-amplitudeCoefficients) int64 0 1 2 3
│             * n-phaseCoefficients      (n-phaseCoefficients) int64 0 1 2 3
│           Data variables:
│               replicaQualityValid      (pole) <U4 'true'
│               crossCorrelationWidth    (pole) float64 1.033
│               sideLobeLevel            (pole) float64 -13.28
│               integratedSideLobeRatio  (pole) float64 -9.988
│               crossCorrelationPeakLoc  (pole) float64 38.2
│               chirpPower               (pole) float64 63.78
│               amplitudeCoefficients    (pole, n-amplitudeCoefficients) float64 1.0 ... ...
│               phaseCoefficients        (pole, n-phaseCoefficients) float64 0.3395 ... -...
│           Attributes:
│               VV_wing:      Combined
│               VV_pulse:     11.58
│               Description:  Chirp Quality Data Store
├── DataTree('radarParameters')
│       Dimensions:                         (beam: 4, pole: 1, NbOfNoiseLevelValues: 99)
│       Coordinates:
│         * beam                            (beam) <U3 'W1' 'W2' 'W30' 'S7'
│         * pole                            (pole) <U2 'VV'
│       Dimensions without coordinates: NbOfNoiseLevelValues
│       Data variables:
│           pulsesReceivedPerDwell          (beam) int64 58 58 58 58
│           numberOfPulseIntervalsPerDwell  (beam) int64 65 66 65 67
│           rank                            (beam) int64 7 8 7 9
│           settableGain                    (beam, pole) float64 -1.0 -1.0 -1.0 -1.0
│           pulseRepetitionFrequency        (beam) float64 1.283e+03 ... 1.297e+03
│           samplesPerEchoLine              (beam) int64 6768 7920 7944 7320
│           noiseLevelValues_BetaNought     (NbOfNoiseLevelValues) float64 -27.16 ......
│           noiseLevelValues_SigmaNought    (NbOfNoiseLevelValues) float64 -28.36 ......
│           noiseLevelValues_Gamma          (NbOfNoiseLevelValues) float64 -26.5 ... ...
│       Attributes: (12/20)
│           acquisitionType:             ScanSAR Wide
│           beams:                       ['W1', 'W2', 'W30', 'S7']
│           polarizations:               ['VV']
│           pulses:                      11.58
│           radarCenterFrequency_units:  Hz
│           radarCenterFrequency:        5404999242.769673
│           ...                          ...
│           adcSamplingRate_units:       Hz
│           adcSamplingRate:             12667968.75
│           yawSteeringFlag:             YawSteeringOn
│           geodeticFlag:                Off-Geocentric
│           rawBitsPerSample:            4
│           Description:                 Radar Parameters Data Store. Information des...
└── DataTree('lut')
        Dimensions:   (pixels: 10432)
        Coordinates:
          * pixels    (pixels) int64 0 1 2 3 4 5 ... 10426 10427 10428 10429 10430 10431
        Data variables:
            lutBeta   (pixels) float64 1.358e+07 1.358e+07 ... 1.358e+07 1.358e+07
            lutGamma  (pixels) float64 1.164e+07 1.164e+07 ... 3.814e+07 3.815e+07
            lutSigma  (pixels) float64 1.789e+07 1.789e+07 ... 4.049e+07 4.05e+07
        Attributes:
            Description:  RADARSAT Product LUT. (c) COPYRIGHT MacDonald Dettwiler and...
```
