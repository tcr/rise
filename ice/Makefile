rise_ice.bin: rise_ice.v
	yosys -q -p "synth_ice40 -blif rise_ice.blif" rise_ice.v
	arachne-pnr --max-passes 2000 -p icestick.pcf rise_ice.blif -o rise_ice.txt
	icebox_explain rise_ice.txt > rise_ice.ex
	icepack rise_ice.txt rise_ice.bin
	icetime -mit -dhx8k rise_ice.txt

generate:
	python generate.py

flash:
	iceprog rise_ice.bin

clean:
	rm -f rise_ice.blif rise_ice.txt rise_ice.ex rise_ice.bin
