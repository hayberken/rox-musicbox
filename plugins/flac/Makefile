INCL 	= -I/usr/include/python2.4
LIBS	= -lFLAC

all:	sw_metadata decoder encoder

decoder:	decoder.py _decoder.so

encoder:	encoder.py _encoder.so

sw_metadata:	sw_metadata.py _sw_metadata.so

sw_metadata.py _sw_metadata.so:	sw_metadata.i format.i
	swig -python sw_metadata.i
	$(CC) -g $(INCL) sw_metadata_wrap.c -shared $(LIBS) -o _sw_metadata.so

decoder.py _decoder.so:	decoder.i format.i
	swig -python decoder.i
	$(CC) -g $(INCL) decoder_wrap.c -shared $(LIBS) -o _decoder.so

encoder.py _encoder.so:	encoder.i format.i
	swig -python encoder.i
	$(CC) -g $(INCL) encoder_wrap.c -shared $(LIBS) -o _encoder.so

clean:
	rm -f sw_metadata_wrap.c _sw_metadata.so sw_metadata.py
	rm -f decoder_wrap.c _decoder.so decoder.py
	rm -f encoder_wrap.c _encoder.so encoder.py
