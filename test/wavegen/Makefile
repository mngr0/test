upload: tb.bin
	sudo iceprog tb.bin

tb.bin: tb.txt
	icepack tb.txt tb.bin

tb.txt: tb.blif
	arachne-pnr -d 8k -p ../../conf_pcf/ICE40H8KBreakoutBoard.pcf -o tb.txt tb.blif

tb.blif: wavegenerator.v
	yosys -p "read_verilog wavegenerator.v; synth_ice40 -blif tb.blif"

wavegenerator.v: do_wavegen.py
	python do_wavegen.py

clean:
	rm tb.* *.v *.vcd *.pyc


test: do_wavegen.py 
	python do_wavegen.py --test
