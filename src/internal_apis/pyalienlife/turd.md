# T.U.R.D.
*As of August 17th, 2025*

```lua
remote.add_interface("pywiki_turd_page", {
    create_turd_page = create_turd_page,
    on_search = on_search,
    reapply_turd_bonuses = reapply_turd_bonuses,
    new_turd = new_turd,
    on_turd_built = on_turd_built
	get_machine_replacement = get_machine_replacement
})
```

## New TURD
This function is the function called when clicking on the TURD select button.

It can be used like this to select an arbitrary TURD, if a TURD is already selected it will deselect it.

```lua
local fake_event = {
  skip_gui = true, -- Need this or it will error out because of gui events
  player = game.player,
  master_tech_name = master_tech_name, -- The technology that unlocks the turd
  sub_tech_name = sub_tech_name, -- The turd name
}

remote.call("pywiki_turd_page", "new_turd", fake_event)
end
```

## get_machine_replacement
This function returns any applied machine replacement turds for the given entity

```lua
---@param force_index integer the force requesting this information
---@param entity_name string the entity get the replacement for
---@return string? replacement_entity the name of the entity that replaces the given entity
```

## List of all TURD Techs and Subtechs

```
arqad-upgrade = {
	air-conditioner,
	cags,
	drone,
},
arthurian-upgrade = {
	abacus,
	heated-stone,
	cannibalism,
},
atomizer-upgrade = {
	sc-core,
	sub-atomic,
	d-core,
},
auog-upgrade = {
	sawdust,
	glowing-mushrooms,
	underground-chambers,
},
bhoddos-upgrade = {
	extra-drones,
	exoenzymes,
	gills,
},
biofactory-upgrade = {
	molecular-polyentomology,
	compusun,
	resonant,
},
bioprinting-upgrade = {
	high-viability,
	biomimetics,
	covalent,
},
bioreactor-upgrade = {
	aerators,
	baffles,
	jacket,
},
cadaveric-arum-upgrade = {
	acid-comtemplator,
	solar-scope,
	e-photo,
},
compost-upgrade = {
	constant,
	humus,
	worm-hotel,
},
cottongut-upgrade = {
	igm,
	ts,
	ud,
},
creature-chamber-upgrade = {
	respiratory,
	neural-fusion,
	cc,
},
cridren-upgrade = {
	sixth-layer,
	neural-cranio,
	mufflers,
},
data-array-upgrade = {
	booster,
	dbwt,
	solar-p,
},
dhilmos-upgrade = {
	cover,
	skimmer,
	double-intake,
},
dingrits-upgrade = {
	alpha,
	c-mutation,
	training,
},
fast-wood-forestry-upgrade = {
	dry-storage,
	selective-heads,
	self-generation,
},
fawogae-upgrade = {
	n2-ferti,
	acidosis,
	dry,
},
fish-upgrade = {
	a-select,
	temp-control,
	dosing-pump,
},
genlab-upgrade = {
	hsn,
	enn,
	dwx,
},
grod-upgrade = {
	hi-sprinkler,
	ground-irrigation,
	carbide-c,
},
guar-upgrade = {
	guarpulse,
	aquaguar,
	hh,
},
incubator-upgrade = {
	gs,
	zero,
	icd,
},
kicalk-upgrade = {
	wire-netting,
	extra-water,
	crop-rotation,
},
kmauts-upgrade = {
	sex-ratio,
	eye-out,
	moult-recycle,
},
korlex-upgrade = {
	multi-tit,
	high-pressure,
	nx-heat-pump,
},
moondrop-upgrade = {
	cu,
	moon,
	carbon-capture,
},
moss-upgrade = {
	spores,
	hd-moss,
	inbuilt-moss,
	remove-muddy-sludge,
},
mukmoux-upgrade = {
	zero-cross,
	bip,
	think-collar,
},
navens-upgrade = {
	cytotoxicity,
	pre-sterilization,
	lichen,
},
numal-upgrade = {
	d2o,
	nc,
	neutron-bombardment,
},
phadai-upgrade = {
	ethanol-boost,
	piezoelectric-floor,
	dubstep-track,
},
phagnot-upgrade = {
	leader,
	socialization,
	hr,
},
ralesia-upgrade = {
	improved-burst,
	sun-concentration,
	h2-recycle,
},
rennea-upgrade = {
	deadheading,
	alltime,
	aphid-cleaning,
},
research-upgrade = {
	unstable,
	ms,
	spg,
	mci,
},
sap-upgrade = {
	inoculator,
	patch,
	bark,
},
schrodinger-antelope-upgrade = {
	pentadimensional,
	existential-hazard,
	higgs-field,
},
scrondrix-upgrade = {
	boronb,
	hspa,
	neuron,
},
seaweed-upgrade = {
	improved-pathfinding,
	precise-cutting,
	recirculation-pump,
},
simik-digestion-mk01 = {
	simik-iron,
	simik-copper,
	simik-quartz,
},
simik-digestion-mk02 = {
	simik-coal,
	simik-tin,
	simik-aluminium,
},
simik-digestion-mk03 = {
	simik-boron,
	simik-chromium,
	simik-molybdenum,
},
simik-digestion-mk04 = {
	simik-zinc,
	simik-nickel,
	simik-lead,
},
simik-digestion-mk05 = {
	simik-titanium,
	simik-niobium,
	simik-nexelit,
},
simik-digestion-mk06 = {
	simik-silver,
	simik-gold,
	simik-uranium,
},
slaughterhouse-upgrade = {
	laser-cutting,
	mercy-killing,
	lard-machine,
},
sponge-upgrade = {
	flagellum,
	fragmentation,
	bacterial,
},
trits-upgrade = {
	mgo,
	dc,
	nexelit-axis,
},
tuuphra-upgrade = {
	fi,
	fungicide,
	tr,
},
ulric-upgrade = {
	dummy-ulric,
	heated-pads,
	scraping-bots,
},
vonix-upgrade = {
	evoa,
	uge,
	dermal,
},
vrauks-upgrade = {
	reuse-water,
	natural-cycle,
	cyanic-recycling,
},
wood-processing-unit-upgrade = {
	biosynthetic-nylon,
	sawblades,
	carbonefarious,
},
xeno-upgrade = {
	ap,
	herm,
	hive,
},
xyhiphoe-upgrade = {
	temp-c,
	rst,
	reuse-ev,
},
yaedols-upgrade = {
	sub-s,
	duct,
	humidity-control,
},
yotoi-upgrade = {
	cryopreservation,
	harvest,
	nutrinet,
},
zipir-upgrade = {
	suicide,
	sr,
	hatchery,
},
zungror-upgrade = {
	geooxidation,
	genooscillation,
	oviduct-bombardment,
}
```
