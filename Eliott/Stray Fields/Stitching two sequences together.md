# Stitching two sequences together

To stitch two sequence together:

https://gitlab.cern.ch/acc-models/acc-models-tls/-/blob/2021/ps_extraction/tt2tt10_lhc_q20/stitched/load_lhc_q20_extraction.madx
``` FORTRAN
select, flag = twiss, clear;
    SELECT, FLAG=TWISS, COLUMN=NAME,KEYWORD,S, L, BETX,ALFX,X,DX,PX,DPX,MUX,BETY,ALFY,Y,DY,PY,DPY,MUY,APER_1,APER_2,K1l,RE11,RE12,RE21,RE22,RE33,RE34,RE43,RE44,RE16,RE26, mvar1, mvar2;
    savebeta,label=initial_cond, place = POINTR;
    twiss, beta0 = bumped;
    x_inj  = -1 * table(twiss, POINTR, x);
    px_inj = -1 * table(twiss, POINTR, px);
    value, x_inj, px_inj;
    change_ref: MATRIX, L=0,  kick1 = x_inj, kick2 = px_inj, rm26= px_inj/(beam->beta), rm51 = -px_inj/(beam->beta);
    seqedit, sequence = ps_extract;
        install, element = change_ref, at = 1e-10, from = POINTR;
        flatten;
    endedit;
```

also look at the code of [slow_extraction_east_simple.ipynb](https://gitlab.cern.ch/eljohnso/acc-models-tls-eliott-fork/-/blob/937e7097d7ffba14bd9e5537e39ee7d8a2357668/ps_extraction/east-fast-extraction/slow_extraction_east_simple.ipynb)

We use the MATRIX element to change referentiel

![[Pasted image 20221005091342.png]]

The slow extraction cannot be transported with a twiss, you need to perform tracking
The distribution on the edge of the septum blade make three turns and are extracted on the fourth one, whereas the ones outside the septum blade are extracted in the present turn.


# Tracking

Original twiss

![[sitched_sequence.png]]

### Thin Track
You can use Thin track my slicing your sequence with makethin

```python
madx.use(sequence="ps_f61d")
madx.input('SEQEDIT, sequence=ps_f61d;')
madx.input('FLATTEN;')
madx.input('ENDEDIT;')
madx.use(sequence="ps_f61d")
madx.input("SELECT, FLAG=makethin, SLICE=5;")
madx.input("MAKETHIN, SEQUENCE=ps_f61d, style=TEAPOT")
madx.use(sequence="ps_f61d")
twiss_ps_f61d = madx.twiss(beta0 = "after_third_turn").dframe()
```


Thin Track slicing takes several minutes and is very far from the original twiss.

![[sitched_sequence_track_slice_20_style_TEAPOT.png]]

### PTC Track

see [[PTC_TRACK#PTC_TRACK simple example]]

PTC uses thick lens Hamiltonian.

