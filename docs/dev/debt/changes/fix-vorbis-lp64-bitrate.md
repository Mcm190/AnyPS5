# libSceVorbisDec
## change [sceVorbisDecOpenCallbacks and sceVorbisDecBitrate]
- [sceVorbisDecOpenCallbacks](../../../core/libs/prx/libSceVorbisDec/Export.cpp) (libSceVorbisDec) - on Windows the host `long` is 32-bit: a tell result outside it, or an initial byte count outside it with a non-null `initial`, throws; a sample rate of 2^31 Hz or more is rejected as a bad header.
## add Functional
- [sceVorbisDecBitrate](../../../core/libs/prx/libSceVorbisDec/Export.cpp) (libSceVorbisDec) - seekable bitrate queries use the bundled libvorbis calculation with 64-bit results on every host, preserve its aggregate float intermediate, and round using the current floating-point rounding mode. Encoded bit counts or rounded results outside signed 64-bit range, and non-finite results (including zero-duration streams), throw. Streaming queries still use host libvorbis and its host-width header fields. Console-specific behaviour remains unverified.
