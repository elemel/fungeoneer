## Chapter 8: Ledger Lines

You have entered the eighth dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnome sits on the bottom stair, sipping from a flask of mushroom brew. As he looks up at you, then down at the purse of stacking on your belt, you recognize him as the cartographer from the first dungeon. He leans forward, as if about to speak. With a magic marker and a flick of the wrist, he scribbles a line of credit onto your purse, in the shape of register S. He pauses for a moment, then sits back, taking another sip.

The stack consists of three consecutive regions of persistent slots, indexed from zero. At the bottom is the fixed stack, with registers A through Z, indexed 0 through 25. Above that is the dynamic stack, indexed from 26 (inclusive) to the current stack size (exclusive). At the top is the hidden stack, indexed from the current stack size (inclusive) to the stack limit (exclusive). Numbers in hidden slots are still retained. All slots are initially zero.

The stack is invalid if the stack size is less than 26, which is called stack underflow, or greater than the stack limit, called stack overflow.

Register S serves as both stack size and stack pointer. It always points to the slot just above the top of the stack. Initially, register S points to slot 26, indicating that the dynamic stack is empty. Pushing writes a number to slot S, then increments S. Popping decrements S, then reads a number from slot S. While popping in effect hides slot S, the number in it is still retained.

With plenty of challenges ahead, you consult the map:

{% raw %}
```
(=](RmIO:=][(}R=}#){R}>e3LN*d1jnWg9bKwfu7>#]#}R[([#]}}#{9ny,Ie={
_iHasicsZ=6qc_>WI[#sc1U}({{}#=}[(]{)[[*up1pjfKmgesbU77}c{.]({(V;
)k*>#gN[g#cQE(]tL}YUNF.WVXXyqEge6[K*t+/ZY4)z}#yM[C9QlJJK4OZG9=6R
Rf5hO%yba}QIUZa+3YqF8y:b2*]ZKmoeWg*i4c=H)-Q>#B/]L.#xbZXrI-aK]D,#
(n4s+Cv5}m].*)=O){>hXB=EqwHgqyzyAYX>Zah]uD=oH,(B/dajOo-UxqgrFg+[
[hE##q)[guqqRDw.IRK#9c>9)hVg#8kfIRs{>TdOHDvHLghay7Z)UT,yM{#odAD#
]1T.ty0AsnjiN{NT[.l#F3#d]=yqAyjZF3;=RWAR}[6(Zt#,fmpu/{ieQW;>}dK[
{M;,Ml]>Ky)RQD*DpVsD0ogp9+AM+{3fb(RleaOgub4vFnw.8U>=27.4KJhY*IV]
#0z-/acm(Tan]BF.)}=i)2]Dn.Q*+ifqgoz:}gkvx4#T5#y1#Afmo[{#eX=E.I9[
}[R2>L2qN)Vu6MJQcW5*hWKJiI%EX)IT(uQbYpAGfg,+4CbvRpp5{aZ;l5um+{o#
)TgQ9qz(s[-[RFzO,Be2JCyGO-1;fzG;4=;+N-uJRFJW=D]I+b2e=1zjMIp5RqO[
):jrzTHrT84iHo6v/{gs#V(+#IF*h#>)Pn1sUhYrsHvMpadp>=.;LT{(hZFId[z#
{1{)%X/L)g#}LDJHJfah6#mFFs/=Tv-EbhmGhlQl[v]5=](JO{nUo{1BEiQ93wa#
(]r;A8bYqvy)TwIrS8)=)tIG>=Y}03=GzCZDm8j0vmhGm4gdHQ.VhRJQ4)m-hau#
}VzV=]04Yrm0DxI+3sus7)m(C61#1;MrB.Nf(wh9.Jae5H/K.wCuvNd[KoZM]fi}
]sfN,*Rt#LRYa#AwO{=4{b%KV0-#{Ir*H73RF6[=TXiWqzOhYJ6pd(p.ahCR(K)R
{ODHYCV21b_Rw2*=TN;VETxcXx3;tdNE8zs;8>}z67jAe/EHpgWd9Qcyk-%u67)V
{(CE9>oXbDRls0OHV2BX;zlao*Cq,TCpuCLnlu{3>1CuDz4ml#+hV}6k5B0K.G]7
RFk+D3I5ele+2y,>oKqAix61Vc6h:1FAJ1d8LANKCF#kzZAqIx4./Uex=i=Amr}2
)xDd%>C)R0Vm(woM2ldQoR>W)IkC#M))w(8D6wN5n%#EhrYiZ/VN9Li}Dtl9=w]N
RwVu+z8ww/DnrsRAqg4-H1Jdj%9g>of.Wd+qIWc4M2JeacR(tg49y=o[+ZRwk/]Y
[g#z)9[NE{D#b45WZDF]3-5;;c9zXDvW/3.dE.oNdbx1:+HvJ6JMt=:XZrvbYc{%
=xkcZo+Yp1]ou#;O2W0tiw5%>#m,BU#)zKN{hwrjhVR%M##qVtE/xZEoI[u6M)>O
{ODQFR5}Bw#=7kV4>s6b#>w7m<.p7zuXV>:xH/Iw5:N%mvWHKMF1X.WWN=>(,=]u
[}{5zfYiHfirZIH>uZV9]Xn0LFaL2xp.#RJ1chauAjxReHw5Wn5x:y9mzty/Zn{O
RHf96Kj)g(zRdwZ#.tDUDi+V>Xo#Tve}NbJ*FK+>wA-L0]Rcr#qs/YGDq#U%=A[D
(=F49QIXu.;n9]gWTk2{;,>pfCY{tJL(wCjNO>Gk/aZvYjG}Z]aF*%lRsQiiL:=t
]8Rmoipmk/k>zwF16YLK[nB())Ebt5cCYVY,kgzZaNvHi/zK7=ok9a;RIknWAzt*
(ZVJxm/40m/NEtitY1y(%vjo:kOrDwVan7n,kcbctl{)Eb)#k95Iy}MdF(Xh[x}Q
}=N#[Ev[WQ)G=R[7]R8x{U)gT=6qRJyaD3IoE+rtD=4Za[vK+jyiocVc>{Pj7N]G
}HnrxFVY1F**86rqZ-z,Js8yvq{}HY{X9]kdmv3[w51ri:+;8MrD.=Fa4}V]J)#2
]FpIR#([[}=()dm2=)#{#(R4d-[)}(R[{}##{[#}R={{}#](({{({{)]({{RPik=

#]=}##](=z*,crymzws%CR<##}(}=#P}(=[[#[][(<BA+BJroJVzt){})#{###{(
]cLQl>i=Ri1;.X<F=fnavb0mUZWY[nn/WX4x[vWMYv]#]#{)>=[}#N,*VH)=H4I)
[Dy<+R#Lqp(R[R>Ey8Rvpftvo8K];Dl>RF}d=L0r=C#e#[>Jnd7#7RDTN4u[(v][
)QDZw87=G=VG{TC=oJFnk11EWCu[0Kh7Cv#Hl/wCj3]<ts027/bb}IehM3jV/-Q}
}]Gr[}/{G_,[g2TeRa<{s6X3>(DuYAmF{wM<Ces[[Z#=0FIo5OYZc=Iz8=Hy+[)=
(4H=.UKu/xRd/bv+{Q6Ar=<}gMkRAp.bEne.<YF:%+0{CgNKGGob/Zs8rB*D+W5=
}Ln#H0]]=SX*8uZ0VZ9LZH;,}DX{z}1#Q-(R{=#jL[ki>rZ((gln9DDF5up<qU)t
#:7vL7+<HbGIOp[[(R]=er=c9[8/=/=dj6lGFze:Z:k8z]9N4m<+ab)g9GN%-,{5
#oYJ1D,/A{%qfrUa(HyTg+,=4A+K3e=g]Y2abAuao1+[R:}q)V)rG:jtW}ftB;(F
#p5+<QsieLo;sjQ)nxQX:Zq]chxdgmv/3]2v+v>h}R2u{jVYkbGAqNe+td3KzTRj
(og{Ly/[T%)]:LJ.V0>=-[TkrNHn.87LiC5N2BU7E5odg2T2>/5Jw[TKjL(cspzn
]:L,)HkrMt*YFp>%XRT6{=JxH}yU8s<V#Qyk}q#w#_/ns+[f<XJVZ8cy/uyVrfw]
]Lq+3c{4fhEzgf14cD:Uk/,(1NY(C95TIp7)Y5VHE){1Cl>uU8qws+Rw=b9(9*T]
#%X:]SpLbKO1ZJYX3/.,HZj{<,rz;E-zlhFykcsZM:y6R#/wLZV8)NnZOrJ0_o}#
{}:W=tch:EqR9Uo;q]YHZ8Cjn#2X2#08Yi7(z#]:9[Mf*j5lw8v#Vlc:A=e:}Ug#
#tAj8u)v4I3.t)rzC6cLO,1:sAaGZVBN5uLvh+CZ0znb{)ZjE:#B4q1L3*)hQdN]
(o3;%88lEyqaxi8itW)R8r:CMwg}rBluSK/1l<v27QYOn081>48mL;T%2o)G4*O)
)6hmd<d=>GXi=Y-nFQx,w1z>jRj8M]nV#D,-(L#n<#YsNOlR.X96eic=Bg)uCmd[
=8nN/O%9xBIVVvr<>f>x[cWQJR)tm]W>(1bZF(H#hBlNqR{Hl7Oqw4*(*+C{}T{[
tG3Un<8b9fwmIz*XM0-7//<hH]%(DgUc]cr)),]3LW:2kT#m-G8(KB03+DZ.A18(
Cq{1ov;G}zyfQ)Mm=M[tRcytu]I}<V7Lqm=8VifJ2+qai6;V9oITamV]t-(_v,c[
ap]4b8[}cf4)w.Wh>aRv(OEwhkQZwQq2IJDN[;p7sTJgpMsmO5sA+o8b:gZYelf(
Go==jbz7jGUj+i-ObZRMwyRz<5sT#q:32RWU0TZ9Fl%AGw[H%e#+-]9(}ZXOKg<}
b+#3([#5.>-8.}d}<2Q--<t#9qNwFD(C-<e*[1A;E=a7d=XzEi{nKn.[M/<0x]u)
mR#RVdwRt619nv=<*9I.+VRkaTBILHb[-X%-,Y:T{B>wH1aM3Iqwfnc.6e84G6f)
qmOgH50#]rRc6TNif>oV{B#r<6KhFDMG,dzDNo)<E#8(U%WQ)IqNw1W{XsQ*Rlh}
MXN%U-1%vCgvoRYUh]-(FY<kjfYivZRg5ZJxg<%9#:bL3j(++8]WL;ZCw8[,rU.{
[9]w.##k[=4<V+iqadZU1XYbL8.73WMbUuXkDsy}{7Fj*=fjC](IURC}t](%cM=}
}B)}{Z=q1RFCu3;(FWo,}W[wc=G#)h)sY7X]uK]nCz#+#l}MM{u#]h7{E][cu]+#
(UEQrnwe6d).G)Ar[)qkrO,Md8vr1;5OVlp,3/WaXa;7%H.xE(=FE)H2<XnJj0>=
]kG2ZoFYAMyx=Qn9p}UWZRp]1h;*(To7p=mqU}r.f,T=>GyyoIDwMgwz;+DRX(hR
)=QjuR[]}({][({})#{{({{{{=)}=R{R(]]Rm[)([}R7=}=#==(=Cl{#(]#]##[[

#})]{R]Rv;cW8*axQ=7RR[8=}(]R][=}}[##)=]{(RRA}][}}[QtqqcYR}({{}}[
#]b=V<a}(tXtiG8dWw:-pZs3E4cizsv9U/F:q6vc>/g23(T(<#J]=#}})rwkgLD.
=sJW:9g6orvApV<i1N)7{(cV}s#}wo(<;g}8;;s)2vnk[:<4(FKjjoYbT>+%%M>h
4.Ztj.4]x]D{({m[E6H>tz/kZs3ihlaE,*1w0uGY4:Ed/kp>fggehf1{Lv}=-E#5
,(qE1iylnaAHum5tA6)}Ra{2<R*pjzi}og8]wY}XguyxRg*baIg0(6ivjCdkyU[I
v{d9kA:JFBXo6nHhiFG,IjU60Jx)-[leC5]Nq[t]{:q>dgVZ/=:jo=#Cf)ywK/[e
e+6QK#RX(s9yYxwMTv84DW#zal#bez.dr>d=Y6zdZ}kV<kAof3KNvnm(wR/#GV[n
(kd/qbCpY(+WrIt]Y/=E>c)av>,>lndJ#o7k(W#%:>H)es].ybGR#bTDO#},e/#,
{>6bSC=8yo2KqkG8ZF447DjAT6;Eb8=;:={yh:J(Zkpk=U)>VQV8]x/bs#[TJJ}q
(iN1q>2m0KblkE[F8w*#,xs}aL2G4[%D)v{YHN<;dIJls(8wtR(okLG*XO81N*{6
}{BE;RrIm0X)tF1tUB<Hy1e)[iAuF=fxDU.Rp8gwC[l.5mG)<pDVEwwyWKpBSv{x
#mBqWdu5kQxlWV<CKmeTcynV7-67Fk-:yAO44sKtGB{FG(DFYu3u4RBolZA]T(IR
[6:Q9jpplOyeZ9.1BNpajB;m+aE,cT0wB]ZDwhNsG=k=9y<LF.U,I(.By}#i,yW]
#H*qAlWC#Bw=FQf#8u>*IW]hJo5s4sso2wadiI%Uhf63,H:8{tOw6jvVw#F2O80]
[1.jt{-CN0Xc8=*KCCObAYkEq1ieY5.;q)]rB+##U})YWrY]*Xx#j9N#k[p86D>}
}bOCWytjqWYcwDdZHai{ARL=6)=fQq2u6#c4Es}cZ=%t]}{5gb]Gg6}oLqr7GYA#
#mA[Y)vwp%:udc5q0DKiJyJ/G>YT2nx5>A}K3x=6Ig1FlKTF<oiT0VD}WhK#R=J[
]Fh0;CAm<R72Jlo7aUfwzUC<4v(=7{fT2#c=;[CqD0#Y{3atDaaydTV4DvRDnVa=
#YRkra68Epd.]DI[<+<Oll#}(lN##24<NoxK1KdquQ{7(/FCnHG#1oEyKOkw3tKY
}cJ3zoOdBrHIab2#DU,b%R}VRt01e+zFRFyYIxJQbta)R38H2;wK0,v3GjtRH)C)
}Dwhs[bxJRBb>B*(rQ>+zDY#qxq0#}gw)oM>vBa]Y6v:0f/Q%iB(W%wLk1/iIaYR
[%L(v3BVH*Jx[}CW<X}[X/LK#pC{MI9>0YQ7>ZI}u8RWBQ-7]/o/4yC6ca%Kc(h#
}.C3Y6KXMjCNKLKmp(1hKv=0#f7g);r88wUvxjw;]a=jRG)n3=o}RQLIJjkIZ+NP
=Ez9Q:>Ue</5/(Jf{pVl]TB#+(ibybmiK)m0pfN(v(8j]uTvrxp>THBmc.3s]O;#
haE+)Bd=FzV13Hv0(3QjV8#W#8v;TY]0Z6g:h6DAdC<#7+gp.})sGiawdnIOP[]#
NvfKvrf]0Xl)MTlYy<[79F/yeKFKyV77I+xxIN,Bo*xj=1FYw6#)E}yyrU)9>(D]
5{(]-=s/FR0])RvNB;L{Tyz[#-U[kCKo:;yhlE*%(K+:UMVDQQl.Ej6%+QlFrsv(
,}5C{nreJm}UGs78Kt{DGWM*{:Y#l9J]T#ccY/k4V.+w9nnvQu5a6)y{KJ>=+=z{
W#qnYN2#dZ({)6v/6h#Sm]Rt1Fm4V6:8Gq/[[Td)gn(32aE3m1#ia{[(Iz8}%hA(
ux#MGWB(+Fg,GMfc#R{#Gn+HEpJ}sq6ARiz,Wp[Wuoi>i{]JlA{[z46KA(5}((<=
W}OC=ztp=ji+uG]h+IVN>D8hN9Az*cnaX##B}hf>ovQW<(TQcpyqK4Ag8r0z,7C=
([##})}#))#{[=-8FriDA63[]GR=]#{##}]###}}}][R)({{}lVz=})#{})#(#(}

#]}#{{NYmofMvNgUh==({(][R[[})]}{](}#[)[)}[#]#]#{([###()[=#})}}(_
}Z2+N:Te4m9R-l,d4B8+8U,RwFUNsH8K/*zo5us;<W[q2S+QEOt(/hT2I3mi}{j)
)G#RvQwrXnUGKH5o/v.v=6U-=>-*FH]F=LbpvO[A(7I7.G+*7DRB2A=}2<x9b}<[
]rj=KO2HimOrebo51jw<orHQ{b]]9JnFBZ],k{BQv9](j)H<ORe9Vhb=L/%j1>}[
{y*{my####z##h)1>mmrx9.*L0])JdUxF*[>9c=Q#M5{]R(=Z)YgaH6Rt#sG}1:#
)}GJJ#;####9*/z#=#[)Xpiy#pCRY){Q+n}#BO;j,#a<mKR9UNE0icmTsgEf>i7[
[/tmWeC-3pqwBL8e7I6QIeW.A6FmF53OM<=eiGRx]7%86QwY9nh#jgsJ*ju9[C({
[D=Q6noL]#o##Q:###tf<Q##/<[<NElFUe#JQRAOq<1#EB#)Kk3{p],Nqb3mYXN(
[<exs(dxlYo:IYp8]}Jk0QEc8V1KL3j.on=]Eo{TTmM*v{+<A-irp)xNXNUvx(H[
[gQ0/<m0e%j)#Zrj6#of2]A##_xtY=OE=MH}#I[A8uA_r#}0pYcpeA##OXKR};#}
#-#9W{[];}[+#(pbgO.n}i#k#=5ywv}:DS#g#.6T(DR:s.=]yoJ{:>QU1ikdk#}(
=G6#Oi[l8xN]W}5J[8P6o#6#6)vlJ.rjx+#yxtjTfhc#mF=]Ts{6QYn]V)KC;fM#
#n#hi/;K9#ZFm9.tJRruVJ}VluO[a%);uqFFeFg8b(#uRr4{/1bJKdaV-;Mw=e=)
[:fAu(zmRc8#fAuX8v<;],htWGO3e5LL[3n9n9n7Z}/>6C1)5wz*>L%FO(RM]{=}
#e=0dDgpi{Q]}WiV{2+BKxG>nEfa4c#Q#G#mH4No##-9xn9;g,QXx6I2.j.}Ot<[
=-mKiewK-wQ4q*z0VR,CVU2Z;FH7goXineRoT9eUr6to}eJm6AS:F4/a5pk}e{>}
ix#TZdvZ#5k/;=MB0%bc+9D6c<TI6:[F<0i=BQeyYyjqFagYNGr*BqC1*eECFnWR
{zoA>#x3c#p5)Xfu)e-8VOYR{7=#0)qZnMEWndkKB69##GWaTTs=>Tu9mj)5JCch
(lhytAKo3BhF7[X3XfZ+TwRD{*>K9:3Rb8t6TE}co##5[JRs(iOlGZ[B-=Dop(f>
=Rp#L(n5bNn=W}Wtx/6.{vjpnM1{EnKz8guXQLy3>i#)MkA]]6{#a}.UN>A%1I+[
#t(#{C{k[WVx<KH}qg<cy)DVGK.TwU#oXX]<)H[If}+fMEs;MfNL%y-tVw.LC6z(
RQFWJIzQg{2RaTjSx}Z503%Ob.T;*ug<92n=<H0DWmcaX+/309jA2Vj[A.H>m}LR
dqh(=;9tTRwwwCp{c[Nw#%}mD3I7RU}z;Cc.=2}:(Jx)F8a(6R9)J>jgbcZ6C}Wg
e)qRUg<*fd0nNQy5=x)Rjadi4hxd*}E+oBp>Gil3A5LoahgK-R[<L;f>o8=RY}HL
FRXRQA8eU{29o%l9WOwM,L2JF>shUo-VQdlF]Z,Z3#)jfnX[Ie}RyhDTkd551=so
8Rf:nijxC}+gBk=GUO>x:ZXMlYnPbj(l=A*8bQXZZ-;o)/=ZYBUGmA%pqEB*<wq*
jXBzQI1s##RG[aNn=;F2)qv48r+=i]Oi%Fa:AdQ}]#i#3s9Fr)dveIj4)x-T(mhC
L0PIt;aD}6ZbcdJ1xiT6s05UM#{pN1p6}{XM>mcn:FYtfvrvX0Kln>Y}Xm<d3.ef
hURoTE2r[#NXkA#oQ>tZJQv]a4j4bMUXr#e}BD[7]##)mgY#[r-9rtK*kfP]H.L1
1UG6)*dkj#D(=,7h7[tvlnN###k=(1(O=I>.zY]y}##<t]Jf:>.4{EdV1y7ibH0=
=2bz67DbY/M0wd-U[.)c<nHrXdO1o=rk3}>{#g(<UAg2a6c*jJ1jfN1CXdc.,)h{
#([)}R}}]#=x*GnxyJW{{}]]]##({Rd[{{_}}(][#R({##[}R[#=_{})]R[})}{}

=I.sz2>)}}(=0D][R){[#]){#=]#R9}=){_#[(([#}{(##{]#{{{=#}}R][LZER#
.#R}##O;)TcDu0A,s37g1(n>9j=g:AHWT:E-{Xg#]a0%>;V1Ah:CbrfEHuIK3o4=
y#ZU#o##4{iU#T}aR+NDccl44<aqrX>=nq)#b5K##D)m)iez#>A33,5rT>orX{-l
h)Ca>iiXU0->:Xwc%[e.Fr-Rc{LuY[Y[6rv>#{c2#8=5:(/#1#f[0z3]Yd+ia<kh
z).4L[dOFKZ4U73H<b>X/4)j#)4>].a)f}O<###YOpGb)>8R:][e;uYOhMKTiRYM
N#s9]ND#[#A)gtm#+#7)dq4n_W7ACElT:U0=###3My6>GRktfTxuH(,8%(4{<m%]
=.NJt9Lfu]wA:fFnEsOEdckMfqZxDkdQNe,}##w#GeN{A#*#FQRNNRb6]2y*n(C#
}))i]#i#%#[7ZlH[>>5L51DC-Y0q3c,,KzU>{jDO:*a4z7f#Rn{Ejb:%=Ol{wc9}
4]-+#wAbw]/G#Hnxr;6-#/F*c0ERd2RZ:Yp:J(0x),)FIJQ/i%Lb2pa1Fm4awuN)
CIaspexk,TTmLo7Bsvk6;-Jp*q9+;TeBJiQ0eKq5lXHck+/Mrf)galmzle+szE-[
9*d*-UF#jT#7+)V[Ow#2txJKdHF#z#+>E(]d0((Y;k##4[cz23w:a<2nX7s]#/F}
LLeL.T7W2#(=yoS2Or9rp+950TfXX.KtIkh25chpWG2Z9;N={i#6p#B53BjT*#5]
D>[>QEZu0=Tt6HiU}op5FW0,##If6#M#>GBa+NLhdX]#=lvQEcA(M+cQL3AU:Yn]
7{G##wIwwpER#V2#/0{rBQ.,h#4,7w:l{.#[#f;)UVT<h6Xt3wUB<QkiWf6#DR0}
C#5f(se1U.#91w42V+TTsLN<:BdurfmRR:7kG*IC;[#zs93Y9t82ynBuWJ-65x{]
X[=TK7616mvRtAvkd6+z:nh#A3q#,rapFZ[F#c##Q#/{q95s)R0a;xWq>5FDR6<{
u#Y)=CzsgUNky=aIwzr=#F2y]46/kY)ZuB0FAYp8/h4e%(zW>Vx%[)5X9ohX5bz)
h}b#<dg#MdOzym8XqmXi#yv#Q#urY###Hd#l#QJ#Zr*zW)6y(xzj<In]1KQ#n(Z[
bvu3QUtHgzKr=8flVdaO-0g>rz<vUX[,#zq(%pc/g/W1jkIOCAXo.J-#Vb9lm=G<
E;eUd}+OU#Zcy6sYh=#(zml;TaeVT1l1#6#-Ban*<;dnNA}tXh{)i2:)-<md0]Nd
E=WIv#uR;X,bNl3[Xd#H#q5G#}[764yFqTIV89rHucL9:gbfRij91]Vx0eh{b(T4
a)VEKt/#aqpE#o7p2#r{#e0z#G#;1lz5IArU7s#E+S]qe0_{4LW#(57(ti/<p]ZM
z[,[1=j[LiEiU#Y+-L#vAhO,#HyLZ{.{5>VcGKI4V1jf0La=cX:47<Ff([r(w>dW
2#1mF*pG+AHDi=#j.Z##-e-ED31x#9l4#>)<[8[#WqbN->]KH)pq9A*<zN4ERUAb
I}b41)=;mFUl3KM+A6.5sru*W<FqHA02pKBDo,wZkkM(vt_o{{qsJQ>o)RHUx:T=
m#{#R7}vY4##s#5j/l<WHG>IGQ#u8sclX--)=vN*-0]2:Kh[#(kv((fss+oRXx.(
p###]vRA2>1bW5Aez5oT.e#uw-[L(Bg#WUd)#ufb(z[Wu:JjqW.bX02c-}}#qq6{
+####436d%##8#=#vQH2]C6f4Wwj0*CsTHZW<6{]3}4=yj{{2gR==<Z-bC/2ox6)
i###6#E==*g9T2H0d<(>pLFr.T_(R6O.eN}2p8>:.uY6X>wwCk7b]}%{109fwR2[
W##+#(C##>5#V#[GdEQWCQ-mdtt+/44ZMZ<duhYiDKfep[c({<pRqmzVf](z}(m[
=37Qz44iJfRAjN2y>[#X)#(>[URbR({[]R<#(P]5VIhgShO[bvQzj4uUCNrnVzY}
}cWnRZRJ(P(}##[]([RQJ+:6MRotpA*ukK0OJ:z({=]#({##(RY-({[#{{#=>={#

##]#)]<LyrRwOauZEC4)(##P[[4wT8=##](}#R{{=#)#}(]{)[{{[[][_}[6MBR#
=IA>R+V9}kUu*MF8sh3aOgJ<V{-g5qVhFawZiEHILfCX<C>baExw05>Vry28j04R
u###U.q{RC+2k+v7Ci,:cmnoTZd>##<E>7v-t9Dsv(Q##=}J6<8vhGMJj<]a#(t}
=kud<Q##8h=<u5eBBNeD:XUdvjr9fk)I#]><D;[z(/V81=NNc.)G]HU+jQmdNce(
T{TwIU7l0EI,jB;bdd<c#=xyUBl<[#/#*RLiNsNOxo.B2<+v9gKI)->h9U4/Q2N=
a/AwHg.Q6)gX(p#-##C)Q=U9HCAep0j3#=im#[O3-[z<)J6zwFZFK74:zw=Knt)}
[wn#GI#.EHt3+#x#u2#w#:#8a[p:>}h(U*1mquedrl%hc;hCNHqbj{Nv4[wx.5W#
=,#;#n##+#K,%-#/<<{3cVm#z0MQ=+m(3d3<6RidNfUGTt=g5m:*8-upWRI>##Z}
[30Y5aL4mp#j*I*(6F#I#3#(A(d.hYc%jWEizcmGe5LEXQRlKX=eJw.#yJ8###Z{
(+m;awdjAWaUxj:4juNrHGka3{p]>8][/[:*)1U*7e]*n.pvd2xRQFNDFi-[*J*#
R5#Ef4f*l>c)#5l:rcRo([XM}#u7l)*<;[tYfRK+fgxw{[>9:=U)D)mGjJBML1>#
):##4op,-OTcCc6t;LXGJend=re4H]K5c,-nCR=t#Fg),I%>qtn:bj*1bmZxuF4}
(<V<)y%#N;u#TI#]8#=DjMAz4W)u}C[O<#.#+o]2:V6:9Mkum8nXV>AYQ069IBG#
{C8s4g#}NkJmva##U3(173#;tw,H5dweQIoG)V_g)L[xCW;%}{sRf%[]4]2x)]R]
[IU%InyIgUYFiH>2HeEV,5,tryDW4*9vrD*Ur8nVd0N*q}e1G>-z(*Y}JWAK6Zs(
==4t#Cz#4slR0K(*)fDj#]w8:##)}lR=t71#*)T3q:uZ6T/1aZ+I{T.T<1,Lrqb)
)w*T;JUZszqxKWAIg*oq,opG=#-ZsoZ-CfrHH91c4{Ewncp]<}>;3LD3u/i/=50[
=Ys7ZucEdI-8DpIGGy=DCA#0Eh[e[JnXhk3I./v/QmMHIQ4g=Z])]nU01b}(g(C=
#-#*#vu9E8DS5t}FF#Ap]E.<z{Wh]}YRf*MOAn{Rvb%C27{tj(Nd)qw5ajBWk:W{
]Ym#{Xcs>[%Gxf-z7lejvoMpn.qmOrJ+Bbxl38l}.{,%rATO:mY-kFR6=#=(2hr#
#j##OA{#f;tPW:>(hm1RU/Q>.gmIR+h}Et0[*t9dw]{;[MG#iG)=HHFb+g{QUe=#
#Q1[m9R##INyC(g(>c#{C0#I8ztiAlE)kqEJ8jn,V7oIehxyk-wwRZED9IftQGD_
#>z=[vfa%R=*UHQm:jLAgHNWsF(F:C1xp<MqD/X)h[/TqI(0Nd+pHXgcUjX={<{#
{H#zXD)Vb+e#C#8zc#GD-)bXgXMvLG[KL<[k*zLEq7.j{<O]tLGmK=J/W/Ds8.#]
#X#;#uDAj7J##QW#P5TQQN{j[B#b>ly5D;pwpMwGC6=E(-#[v-e7a;<b::GDYRM#
}u#;#}C>hk*Lwb4OHTDWgD<-(n]vC;9]-OmDozkp[.DD8>#g{HR6NIBW-:BgNzy}
#ccxDl}nb<)M.od8gMmp-OR64Xm/[wxW2p0-ye=ssv1Rs:Yc}YKimW{}#{284[3)
[hNX9B4qrh%jm#YN/})oU#q}BB72usL09KjCopBXxfF[#CI(YzxXnR{s}9%dUdR#
#E#O#J#E#)UT%)m#1Dr<U-#5aw#d)DVJ2z6)lE<EA3tmX<-a7GZd=m}oyCcx[91}
[Oi%>X##w<#]X*.t8#N(C5)qHt0YX(M8-z9wf%#6(=Ak[bMVs8}]5u#reZm76[i}
]o#p#J###;7MOomg<aQ8x[R<{=RRoV}oUIwR2={=wY](#NX(Ahp3k)=(+=W1o=x(
[{}}[=-9.=(#}*R4*8=)msDR{#[(=#{](}}_[RU6Fm;{}((=}=[R{REy+{}(<>-(

#=ORK](#=(n=(###R#}R[##R##{#)}{][]]}}){)){###{448R{}###{#[{y==)[
]Bz<.GU;#H}T[(#s)lqxF-J91Vg-FZbf%2*m*>g5S#X#RV<J=xn0Bu<QfY9JJ=9]
]0Z5o9]#}y.Qa#Q###,H0#e(#V)<N7Gu<wxccIu0AsMvusui.Zf6WQyI5e9jr3C(
#Rj#RL}]#>#K#n###j>W###r#VjHTp{w+]<]qL[HL9N)=#u#iLwJ[InHKx%jsTE)
#t;>x1n#0}7#d###tvtw###yI#X,{BeHakra)zC%(>l7:yK1w;a40g<((x(E0eK}
R6wzO]Zr)A-amvZgUOb1QiBO0:cII{n{LtDKp>EoP,S=e(]#[aVjyBef1#A#q[w}
#V3]y.Q1penq)[E89##F##DYy###<}=hZ8.{ed:r-q67FV8eHUFV>j(7iI#F4(/(
#Ce#nn#>EWZ}BHKe###a#+#-###a##(wV#}=H)R6WO(42s.2Ae2fk:oj,#}<1dw=
(X#*Q#M#/>hz/GCbx0BhUTBWzYsfYiTvCa.)V_M,-]T+L{o3#hJyWQ#]Y=zgE(K{
#s##/##v#;{l/{#####/#W#b#c##<#-v}>Ny92}2GzzNNIMaTRlL:yVvF.8VH7n#
#h##yoIeB<;Fjrb###1nQ##GD##W#1#R###:ApVuqmDFbO<;(FWn06y7TX3v#4<)
)p##a{q##0/#b*Ms#Z#t###9##5#I#iZb#[8Y(#y:V{#]Ox<R1nMbF#F0]]xt][]
(w.lhT#HO2Kg9sp2Z#pN#{/s0goBrv1h9-y(qW5Uf#5#RC6xybC1;<DKkpGo{EQ[
=u:3)A#QM(gtHR)c.Y#o{opI((d>LVx=fda*oVW]#]8#],(EJKDw77zFcE23)Q[)
#f,K#KmX]Y=*ac<2FIUeftK7}4#k##{c5#:#4e3Uz/.[dr,b><B(mp(O;;J434x{
#4qJY9(oB6D)DL#.#Q:x>061[6GtEV2Di2lgcrV=B0Ya>lR-hl]Iee5]YhRmetM#
{8#=HgbMK[%BiFg+d+WW6[)qk7#L=Dah-)GV3#T+)sn*:=a]M4<8kT7hf##=Tbe[
}lLAx#=C#Fe#xE#GDV#iQJ#}Dk##w%}7#G+DTb#Y#;%Yvbj#{lRcn{YH3p(G38;#
#:IA[3}7*#g{6gy:v5XIbAN1LUD*8H38}ez#/##M>WhwTxqO-g%aCK+{]{UE#v-]
]gh{h#4f<w9jT3tGTqkcDps2/ch}t[VJmcls5##h#e#X{M=5rC>-[,u]]t928gj#
R*I9qts2O;%w=E<1##y._AX<Fb4zU2jE-#x#I##pp#N##C>7vI{KT#uLUn{*W0v[
R(h#02LpJnC#W##l<##zt[#5eIE#g*#F[Mb#tZ#1#z##>gDfZkUKT{Lwy#Y{/oBN
*<>rq(o0,]1n###d9E#in#w+F{f-DsL/U#H#O#cFx##T[%###5*C(coG(5#[#UC4
uw##E#Eza#d###gBsW6Q[x/VIvOlUR}Y#HanEp#k##a##2f#ZsQu+ozR646nJEaR
3E{,=da{%d9##{8XUgFlEC8hb+zx<T%x#]*3n>dzV0G%qu[qPls+MC04zvOV[;-]
:d)w3N9<FhN[###37#=Dg##V:4J;74H3zUd1TtR%{v]R#<R]-F=B}wd#e7UC2bd#
xm#h]f3Cq]xO[BLsoxx8j[rBthpe7lz.o-*#A#jn##Z32osDE43gDaU2/H::E3GR
2u;L#ntRaN(S#w2#Z)Mss26G,8swD7b{kk}X28#j8]Kv}bw=(y3#toX#mKxx#+4C
(-:zc20(Us(a#Z#]=XAuAAbfoge.laYvVX*f%s7HZCs9*Jc1Vb7thxje+Z=rCoEk
}E[;<YSFLF>Ij5>#B##(c{Owpg{k)8+2>G{%R3k;{kw-#yyd#]-]JBb9,8EB1V-G
=>ox)s5F28L:h+utUmoT8p}aL[83XQ-JwC+Y%/b>Nv0icDT-scGe]6+[[hB##}2>
#[#P=##=}}[]{([#[###)#=_#=((#}#]####})(({}#]{{][R.R(]3RR44Rp*<d[

#######{G=#[##R4]#R}{)](R##=#){[{{[[=)R)]#}{{{qnnR#}]=]=}{}[]##)
#########D8/KyU0LDz4V=iea0y.It06iV[)E<9=arpkVq2)#4n)Zlr]7X4(0)7]
#########,(d{,%G2RTwed)bn.A##n#rJv6xm9zWt,QwWLKTy0sU{2IsYcr{*4,{
#########<Q###7]0#<yVr]2)##40#BQTY=)b1_xmJE(XuQit1Oic[;9Qo2#X#6n
###<####sE#####f###fYK#a}#R5y]h#w+myx[mW)<(BA(t7yqqq{=RKfk{fm#lR
####J##miL####2#o#r#qa#Djevnbo#/#CK],<=wgMW7T+om;xk*6).CR=p+eFk1
#####T8%#W}##C###d##Lcittf7B%f;##NLHmmmM(=#Ih-C):cZR<V7XMDJ2/M{Y
#####U+<#2X#G###p#-#w+#%o#zF#172#6ZwFgcKIP9gO#+XUwr*{Mju,LH],Zxh
####M]o##<Gz###3###Guxkvhyh:S#+p){h{vyi7=[]%Za=3*r.8OQ8L(]/RaU2)
###t#e##=#b#;#H####}3x[vHn=sMfkp%<b3p*b{euO#v]+g72jCAvh7{a24[rsP
##a#6##1#=#{#G####RWseW8b(A##%#yD]-lkL/.xN1dQ]T((Q]#s/W}n/m#Q#R=
}lWIN*G8Q2*#ERuF8gi,R{fNa#{5##E6Tld26Cz}pt9txa;0kXoze68TQEL-Zhk)
##Z#)0###m#RR/xIXcd=)B}Z#:#[vB#.Q7(nTi_{=zu=%-G}{j9(Xwvz/emiZLV{
#K#WJh1Y7Vtj77:R9C}*x#0#[.4<;dX+an)#Y#f#b(URqv4wsirwx]*2dwRi;k]]
(%3d###k#+#:##V#C(#g[TflmW#b{XvRDTqMMcXN{,ZG5(rr<tlN)cv3Y*JL2GH)
}Z-##}3#v##s##}6w8,R<hw#KG.#0Zr+#9t#F#L#{xj9<x}I}+h##{FW]*A93LJ}
#4F#8A#Z###8##5#8N#x#a#D-I=Vb.8N5tOCN4QU]U:IO1EJ0;UFp(BoaVIkwRn(
#{#jv%K##]#q#Z##H*##mD/#Nr%N####+T##d[i#9RaB-o{ZNq##B}w7Ge#{C(U(
##=58W#MB##%(b#D##r##d#McXrOF##txX*R;Oa*<Gk0OI8%svj#w#5N]ctZ#r[]
]#;C}##X,N#7#9;####0H}ukw6f#jL{##gpQbow1}(4A-wd+iF<yYWzUXU301Vk{
#H##pgNICqfqWgumjIpaY196R{]%#EX##i#RT[:6:H,He9<p#F}#H7wl{rrkv=#:
##=##+1###x[Y{+equBzAeOk.0*LnLVKZY9Ziq]#Ka(/<R.}8i8hd7jO]OT+spY*
R7<Az#NZ##{p##G0#FKf%vD#m#W*Z]7/Ahz/U+iR-kC#c;6Kjiv),#5k#dhVu/)h
=L#cX##mj#2lVs:8L:(16##6##*OJ8/bEAbHQ({*r-{b#(wXdTI:FY}ja1}lUV{J
[GH{+r-Rx1{[Z1)#B[rvp#K#3jI#H,_#[7rJN<G*QsCLeqD#,zT)(T#Gl[[64e(a
#R57Bmj.FKa*VTt##Yty)d##9sP##cN(},00U##}{9#[C*J7#Kf##=lLcK57)z(B
[70jL(9tpBC1HI,eOuMUdtnLoomK9:x9DZz]*(3%U}q,##m#JVd:#AoT](XJn;L=
[A2psF[b=#A:[##4VI#M##3l###m#x#*1}]jwYolkxMgQkmvnbl+L{#nF55X[(#=
#B##}MvwH2lzi#dVMl#{Rf+####[rFsI)sg,oH86ltwaH(RkztF)c+;%W.fl/B7#
#b####g0,R<I[a<O#tI#==#####.)%6]<N3wZ:MIrH-v/ZaTmk58y9dQKJ9=+tXR
]<NwJLOykfExdrov*tv56XAqu:OjLj9r]Xd=b.0<+uV*syY]06x)/##V#lj}zw6<
#(}###_#{##{{[})##(R]####[{)[#{R{(]{}yf=#R#]))({]=}]#}[){=R##R#]
```
{% endraw %}

This dungeon contains tiles with peekers (marked `,` on the map) and pokers (marked `;`), along with getters and setters for register S (marked `s` or `S`).

Whenever you step onto a peeker tile, pop an argument `a` from the stack. Then get another number `b` from slot `a`. Finally, push `b` onto the stack.

Whenever you step onto a poker tile, pop two arguments from the stack: first `b`, then `a`. Set the number in slot `a` to `b`.

Whenever you step onto an S-getter tile, get the stack size as a number, then push that number onto the stack. For an S-setter tile, pop a number from the stack, then set the stack size to that number. This effectively only changes the stack pointer, while leaving the slots and their numbers unchanged, except for which slots are hidden.

After how many steps do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/08/ledger-lines.md).

### Example

Consider an example dungeon:

{% raw %}
```
##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#
```
{% endraw %}

Below is a log of walking through the example dungeon. The hidden slots above the dynamic stack are shown as `(n)`. Your location is marked `@` on the map.

{% raw %}
```
Step count: 0
Coordinates: (10, 6, 0)
Direction: East
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (0):
  [Empty]

Non-zero registers:
  S: 26
  P: 106

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:@48{{)
([}#)}]}[#P]RRP#

---

Step count: 1
Coordinates: (11, 6, 0)
Direction: East
Next symbol: 8

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (1):
  4 [Top]

Non-zero registers:
  S: 27
  P: 107

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<@8{{)
([}#)}]}[#P]RRP#

---

Step count: 2
Coordinates: (12, 6, 0)
Direction: East
Next symbol: {

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (2):
  8 [Top]
  4

Non-zero registers:
  S: 28
  P: 108

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<4@{{)
([}#)}]}[#P]RRP#

---

Step count: 3
Coordinates: (12, 6, 0)
Direction: Northwest
Next symbol: 2

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (2):
  8 [Top]
  4

Non-zero registers:
  S: 28
  R: -3
  P: 108

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<4@{{)
([}#)}]}[#P]RRP#

---

Step count: 4
Coordinates: (11, 5, 0)
Direction: Northwest
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (3):
  2 [Top]
  8
  4

Non-zero registers:
  S: 29
  R: -3
  P: 91

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p@};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 5
Coordinates: (11, 5, 0)
Direction: North
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (3):
  2 [Top]
  8
  4

Non-zero registers:
  S: 29
  R: -2
  P: 91

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p@};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 6
Coordinates: (11, 4, 0)
Direction: North
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (4):
  75 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: -2
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 7
Coordinates: (11, 4, 0)
Direction: Northeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (4):
  75 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: -1
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 8
Coordinates: (12, 3, 0)
Direction: Southwest
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (75) [S]

Dynamic stack (3):
  2 [Top]
  8
  4

Non-zero registers:
  S: 29
  R: 75
  P: 60

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)@5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 9
Coordinates: (11, 4, 0)
Direction: Southwest
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (4):
  75 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: 75
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 10
Coordinates: (10, 5, 0)
Direction: Southwest
Next symbol: :

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  90 [Top]
  75
  2
  8
  ...

Non-zero registers:
  S: 31
  R: 75
  P: 90

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#@2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 11
Coordinates: (9, 6, 0)
Direction: Southwest
Next symbol: [

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  75 [Top]
  90
  2
  8
  ...

Non-zero registers:
  S: 31
  R: 75
  P: 105

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#@<48{{)
([}#)}]}[#P]RRP#

---

Step count: 12
Coordinates: (9, 6, 0)
Direction: Southeast
Next symbol: P

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  75 [Top]
  90
  2
  8
  ...

Non-zero registers:
  S: 31
  R: 73
  P: 105

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#@<48{{)
([}#)}]}[#P]RRP#

---

Step count: 13
Coordinates: (11, 4, 0)
Direction: Southeast
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (75) [S]

Dynamic stack (4):
  90 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: 73
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 14
Coordinates: (11, 4, 0)
Direction: West
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (75) [S]

Dynamic stack (4):
  90 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: 76
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 15
Coordinates: (11, 4, 0)
Direction: Northwest
Next symbol: :

Hidden stack:
  ...
  (0)
  (0)
  (75) [S]

Dynamic stack (4):
  90 [Top]
  2
  8
  4

Non-zero registers:
  S: 30
  R: 77
  P: 75

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)@#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 16
Coordinates: (10, 3, 0)
Direction: Northwest
Next symbol: 7

Hidden stack:
  ...
  (0)
  (0)
  (75) [S]

Dynamic stack (4):
  2 [Top]
  90
  8
  4

Non-zero registers:
  S: 30
  R: 77
  P: 58

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.@)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 17
Coordinates: (9, 2, 0)
Direction: Northwest
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  7 [Top]
  2
  90
  8
  ...

Non-zero registers:
  S: 31
  R: 77
  P: 41

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s@639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 18
Coordinates: (9, 2, 0)
Direction: Northeast
Next symbol: .

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  7 [Top]
  2
  90
  8
  ...

Non-zero registers:
  S: 31
  R: 79
  P: 41

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s@639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 19
Coordinates: (10, 1, 0)
Direction: Northeast
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  7 [Top]
  2
  90
  8
  ...

Non-zero registers:
  S: 31
  R: 79
  P: 26

##]##[###=p)R={{
#[r44R3{]3@5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 20
Coordinates: (10, 1, 0)
Direction: East
Next symbol: 5

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (5):
  7 [Top]
  2
  90
  8
  ...

Non-zero registers:
  S: 31
  R: 80
  P: 26

##]##[###=p)R={{
#[r44R3{]3@5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 21
Coordinates: (11, 1, 0)
Direction: East
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (6):
  5 [Top]
  7
  2
  90
  ...

Non-zero registers:
  S: 32
  R: 80
  P: 27

##]##[###=p)R={{
#[r44R3{]3.@]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 22
Coordinates: (11, 1, 0)
Direction: South
Next symbol: 3

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (6):
  5 [Top]
  7
  2
  90
  ...

Non-zero registers:
  S: 32
  R: 82
  P: 27

##]##[###=p)R={{
#[r44R3{]3.@]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 23
Coordinates: (11, 2, 0)
Direction: South
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (7):
  3 [Top]
  5
  7
  2
  ...

Non-zero registers:
  S: 33
  R: 82
  P: 43

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s76@9,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 24
Coordinates: (11, 2, 0)
Direction: Southwest
Next symbol: :

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (7):
  3 [Top]
  5
  7
  2
  ...

Non-zero registers:
  S: 33
  R: 83
  P: 43

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s76@9,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 25
Coordinates: (10, 3, 0)
Direction: Southwest
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (7):
  5 [Top]
  3
  7
  2
  ...

Non-zero registers:
  S: 33
  R: 83
  P: 58

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.@)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 26
Coordinates: (9, 4, 0)
Direction: Southwest
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: 83
  P: 73

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#@)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 27
Coordinates: (9, 4, 0)
Direction: North
Next symbol: .

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: 86
  P: 73

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#@)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 28
Coordinates: (9, 3, 0)
Direction: North
Next symbol: 7

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: 86
  P: 57

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4@:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 29
Coordinates: (9, 2, 0)
Direction: North
Next symbol: 3

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (9):
  7 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 86
  P: 41

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s@639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 30
Coordinates: (9, 1, 0)
Direction: North
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (10):
  3 [Top]
  7
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 86
  P: 25

##]##[###=p)R={{
#[r44R3{]@.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 31
Coordinates: (9, 0, 0)
Direction: East
Next symbol: p

Hidden stack:
  ...
  (0)
  (3)
  (7) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: 88
  P: 9

##]##[###@p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 32
Coordinates: (10, 0, 0)
Direction: East
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (3) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 88
  P: 10

##]##[###=@)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 33
Coordinates: (10, 0, 0)
Direction: Southeast
Next symbol: 5

Hidden stack:
  ...
  (0)
  (0)
  (3) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 89
  P: 10

##]##[###=@)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 34
Coordinates: (11, 1, 0)
Direction: Southeast
Next symbol: 9

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (10):
  5 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 89
  P: 27

##]##[###=p)R={{
#[r44R3{]3.@]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 35
Coordinates: (12, 2, 0)
Direction: Southeast
Next symbol: 5

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 89
  P: 44

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s763@,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 36
Coordinates: (13, 3, 0)
Direction: Southeast
Next symbol: 9

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (12):
  5 [Top]
  9
  5
  10
  ...

Non-zero registers:
  S: 38
  R: 89
  P: 61

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R@r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 37
Coordinates: (14, 4, 0)
Direction: Southeast
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  9 [Top]
  5
  9
  5
  ...

Non-zero registers:
  S: 39
  R: 89
  P: 78

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{@{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 38
Coordinates: (14, 4, 0)
Direction: South
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  9 [Top]
  5
  9
  5
  ...

Non-zero registers:
  S: 39
  R: 90
  P: 78

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{@{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 39
Coordinates: (14, 5, 0)
Direction: East
Next symbol: )

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 88
  P: 94

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};@)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 40
Coordinates: (14, 5, 0)
Direction: Southeast
Next symbol: )

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 89
  P: 94

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};@)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 41
Coordinates: (14, 5, 0)
Direction: South
Next symbol: {

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 90
  P: 94

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};@)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 42
Coordinates: (14, 5, 0)
Direction: Northeast
Next symbol: {

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 87
  P: 94

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};@)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 43
Coordinates: (14, 5, 0)
Direction: West
Next symbol: ;

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  9 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 84
  P: 94

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};@)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 44
Coordinates: (13, 5, 0)
Direction: West
Next symbol: }

Hidden stack:
  ...
  (5)
  (9)
  (5) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 84
  P: 93
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2}@=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 45
Coordinates: (13, 5, 0)
Direction: Northeast
Next symbol: 9

Hidden stack:
  ...
  (5)
  (9)
  (5) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 87
  P: 93
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2}@=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 46
Coordinates: (14, 4, 0)
Direction: Northeast
Next symbol: (

Hidden stack:
  ...
  (9)
  (5)
  (9) [S]

Dynamic stack (10):
  9 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 87
  P: 78
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{@{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 47
Coordinates: (14, 4, 0)
Direction: North
Next symbol: r

Hidden stack:
  ...
  (9)
  (5)
  (9) [S]

Dynamic stack (10):
  9 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 86
  P: 78
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{@{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 48
Coordinates: (14, 3, 0)
Direction: North
Next symbol: ;

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  86 [Top]
  9
  10
  4
  ...

Non-zero registers:
  S: 37
  R: 86
  P: 62
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5@(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 49
Coordinates: (14, 2, 0)
Direction: North
Next symbol: 3

Hidden stack:
  ...
  (5)
  (86)
  (9) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 86
  P: 46
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,@[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 50
Coordinates: (14, 1, 0)
Direction: North
Next symbol: {

Hidden stack:
  ...
  (9)
  (5)
  (86) [S]

Dynamic stack (10):
  3 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 86
  P: 30
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]7@{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 51
Coordinates: (14, 1, 0)
Direction: Southwest
Next symbol: ,

Hidden stack:
  ...
  (9)
  (5)
  (86) [S]

Dynamic stack (10):
  3 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 83
  P: 30
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]7@{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 52
Coordinates: (13, 2, 0)
Direction: Southwest
Next symbol: R

Hidden stack:
  ...
  (9)
  (5)
  (86) [S]

Dynamic stack (10):
  0 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 83
  P: 45
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639@;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 53
Coordinates: (12, 3, 0)
Direction: East
Next symbol: 5

Hidden stack:
  ...
  (5)
  (86)
  (0) [S]

Dynamic stack (9):
  10 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  P: 60
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)@5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 54
Coordinates: (13, 3, 0)
Direction: East
Next symbol: r

Hidden stack:
  ...
  (9)
  (5)
  (86) [S]

Dynamic stack (10):
  5 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  P: 61
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R@r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 55
Coordinates: (14, 3, 0)
Direction: East
Next symbol: (

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  P: 62
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5@(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 56
Coordinates: (14, 3, 0)
Direction: Northeast
Next symbol: [

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: -1
  P: 62
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5@(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 57
Coordinates: (14, 3, 0)
Direction: Northwest
Next symbol: ,

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: -3
  P: 62
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5@(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 58
Coordinates: (13, 2, 0)
Direction: Northwest
Next symbol: ]

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: -3
  P: 45
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639@;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 59
Coordinates: (13, 2, 0)
Direction: Northeast
Next symbol: 3

Hidden stack:
  ...
  (0)
  (9)
  (5) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: -1
  P: 45
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639@;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 60
Coordinates: (14, 1, 0)
Direction: Northeast
Next symbol: {

Hidden stack:
  ...
  (0)
  (0)
  (9) [S]

Dynamic stack (12):
  3 [Top]
  0
  5
  10
  ...

Non-zero registers:
  S: 38
  R: -1
  P: 30
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]7@{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 61
Coordinates: (14, 1, 0)
Direction: West
Next symbol: 7

Hidden stack:
  ...
  (0)
  (0)
  (9) [S]

Dynamic stack (12):
  3 [Top]
  0
  5
  10
  ...

Non-zero registers:
  S: 38
  R: -4
  P: 30
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]7@{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 62
Coordinates: (13, 1, 0)
Direction: West
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  7 [Top]
  3
  0
  5
  ...

Non-zero registers:
  S: 39
  R: -4
  P: 29
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]@3{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 63
Coordinates: (13, 1, 0)
Direction: North
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  7 [Top]
  3
  0
  5
  ...

Non-zero registers:
  S: 39
  R: -2
  P: 29
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]@3{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 64
Coordinates: (13, 0, 0)
Direction: West
Next symbol: R

Hidden stack:
  ...
  (0)
  (7)
  (3) [S]

Dynamic stack (11):
  0 [Top]
  5
  10
  4
  ...

Non-zero registers:
  S: 37
  R: -4
  P: 13
  J: 86
  F: 9

##]##[###=p)R@{{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 65
Coordinates: (12, 0, 0)
Direction: East
Next symbol: =

Hidden stack:
  ...
  (7)
  (3)
  (0) [S]

Dynamic stack (10):
  5 [Top]
  10
  4
  5
  ...

Non-zero registers:
  S: 36
  P: 12
  J: 86
  F: 9

##]##[###=p)@={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 66
Coordinates: (13, 0, 0)
Direction: South
Next symbol: 7

Hidden stack:
  ...
  (0)
  (5)
  (10) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: 2
  P: 13
  J: 86
  F: 9

##]##[###=p)R@{{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 67
Coordinates: (13, 1, 0)
Direction: South
Next symbol: ,

Hidden stack:
  ...
  (3)
  (0)
  (5) [S]

Dynamic stack (9):
  7 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 2
  P: 29
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]@3{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 68
Coordinates: (13, 2, 0)
Direction: South
Next symbol: 5

Hidden stack:
  ...
  (3)
  (0)
  (5) [S]

Dynamic stack (9):
  0 [Top]
  4
  5
  3
  ...

Non-zero registers:
  S: 35
  R: 2
  P: 45
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639@;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 69
Coordinates: (13, 3, 0)
Direction: South
Next symbol: {

Hidden stack:
  ...
  (7)
  (3)
  (0) [S]

Dynamic stack (10):
  5 [Top]
  0
  4
  5
  ...

Non-zero registers:
  S: 36
  R: 2
  P: 61
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R@r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 70
Coordinates: (13, 3, 0)
Direction: Northeast
Next symbol: ;

Hidden stack:
  ...
  (7)
  (3)
  (0) [S]

Dynamic stack (10):
  5 [Top]
  0
  4
  5
  ...

Non-zero registers:
  S: 36
  R: -1
  P: 61
  J: 86
  F: 9

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R@r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 71
Coordinates: (14, 2, 0)
Direction: Northeast
Next symbol: {

Hidden stack:
  ...
  (0)
  (5)
  (0) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: -1
  P: 46
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,@[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 72
Coordinates: (14, 2, 0)
Direction: West
Next symbol: ,

Hidden stack:
  ...
  (0)
  (5)
  (0) [S]

Dynamic stack (8):
  4 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: -4
  P: 46
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,@[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 73
Coordinates: (13, 2, 0)
Direction: West
Next symbol: 9

Hidden stack:
  ...
  (0)
  (5)
  (0) [S]

Dynamic stack (8):
  0 [Top]
  5
  3
  7
  ...

Non-zero registers:
  S: 34
  R: -4
  P: 45
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639@;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 74
Coordinates: (12, 2, 0)
Direction: West
Next symbol: 3

Hidden stack:
  ...
  (3)
  (0)
  (5) [S]

Dynamic stack (9):
  9 [Top]
  0
  5
  3
  ...

Non-zero registers:
  S: 35
  R: -4
  P: 44
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s763@,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 75
Coordinates: (11, 2, 0)
Direction: West
Next symbol: 6

Hidden stack:
  ...
  (7)
  (3)
  (0) [S]

Dynamic stack (10):
  3 [Top]
  9
  0
  5
  ...

Non-zero registers:
  S: 36
  R: -4
  P: 43
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s76@9,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 76
Coordinates: (10, 2, 0)
Direction: West
Next symbol: 7

Hidden stack:
  ...
  (0)
  (7)
  (3) [S]

Dynamic stack (11):
  6 [Top]
  3
  9
  0
  ...

Non-zero registers:
  S: 37
  R: -4
  P: 42
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7@39,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 77
Coordinates: (9, 2, 0)
Direction: West
Next symbol: s

Hidden stack:
  ...
  (0)
  (0)
  (7) [S]

Dynamic stack (12):
  7 [Top]
  6
  3
  9
  ...

Non-zero registers:
  S: 38
  R: -4
  P: 41
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s@639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 78
Coordinates: (8, 2, 0)
Direction: West
Next symbol: :

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  38 [Top]
  7
  6
  3
  ...

Non-zero registers:
  S: 39
  R: -4
  P: 40
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:@7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 79
Coordinates: (7, 2, 0)
Direction: West
Next symbol: 6

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (13):
  7 [Top]
  38
  6
  3
  ...

Non-zero registers:
  S: 39
  R: -4
  P: 39
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76@s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 80
Coordinates: (6, 2, 0)
Direction: West
Next symbol: 7

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (14):
  6 [Top]
  7
  38
  6
  ...

Non-zero registers:
  S: 40
  R: -4
  P: 38
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,7@:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 81
Coordinates: (5, 2, 0)
Direction: West
Next symbol: ,

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (15):
  7 [Top]
  6
  7
  38
  ...

Non-zero registers:
  S: 41
  R: -4
  P: 37
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,@6:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 82
Coordinates: (4, 2, 0)
Direction: West
Next symbol: ;

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (15):
  0 [Top]
  6
  7
  38
  ...

Non-zero registers:
  S: 41
  R: -4
  P: 36
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;@76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 83
Coordinates: (3, 2, 0)
Direction: West
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (6) [S]

Dynamic stack (13):
  7 [Top]
  38
  6
  3
  ...

Non-zero registers:
  S: 39
  R: -4
  P: 35
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=@,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 84
Coordinates: (2, 2, 0)
Direction: North
Next symbol: r

Hidden stack:
  ...
  (6)
  (7)
  (38) [S]

Dynamic stack (11):
  6 [Top]
  3
  9
  0
  ...

Non-zero registers:
  S: 37
  R: -2
  P: 34
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3@;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 85
Coordinates: (2, 1, 0)
Direction: North
Next symbol: ]

Hidden stack:
  ...
  (0)
  (6)
  (7) [S]

Dynamic stack (12):
  -2 [Top]
  6
  3
  9
  ...

Non-zero registers:
  S: 38
  R: -2
  P: 18
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[@44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 86
Coordinates: (2, 1, 0)
Direction: East
Next symbol: 4

Hidden stack:
  ...
  (0)
  (6)
  (7) [S]

Dynamic stack (12):
  -2 [Top]
  6
  3
  9
  ...

Non-zero registers:
  S: 38
  P: 18
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[@44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 87
Coordinates: (3, 1, 0)
Direction: East
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (6) [S]

Dynamic stack (13):
  4 [Top]
  -2
  6
  3
  ...

Non-zero registers:
  S: 39
  P: 19
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r@4R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 88
Coordinates: (4, 1, 0)
Direction: East
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (14):
  4 [Top]
  4
  -2
  6
  ...

Non-zero registers:
  S: 40
  P: 20
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r4@R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 89
Coordinates: (5, 1, 0)
Direction: West
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (13):
  4 [Top]
  -2
  6
  3
  ...

Non-zero registers:
  S: 39
  R: 4
  P: 21
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44@3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 90
Coordinates: (4, 1, 0)
Direction: West
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (14):
  4 [Top]
  4
  -2
  6
  ...

Non-zero registers:
  S: 40
  R: 4
  P: 20
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r4@R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 91
Coordinates: (3, 1, 0)
Direction: West
Next symbol: r

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (15):
  4 [Top]
  4
  4
  -2
  ...

Non-zero registers:
  S: 41
  R: 4
  P: 19
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r@4R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 92
Coordinates: (2, 1, 0)
Direction: West
Next symbol: [

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  4 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 4
  P: 18
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[@44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 93
Coordinates: (2, 1, 0)
Direction: South
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  4 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 2
  P: 18
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[@44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 94
Coordinates: (2, 2, 0)
Direction: South
Next symbol: 4

Hidden stack:
  ...
  (0)
  (4)
  (4) [S]

Dynamic stack (14):
  4 [Top]
  4
  -2
  6
  ...

Non-zero registers:
  S: 40
  R: 2
  P: 34
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3@;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 95
Coordinates: (2, 3, 0)
Direction: South
Next symbol: 2

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (15):
  4 [Top]
  4
  4
  -2
  ...

Non-zero registers:
  S: 41
  R: 2
  P: 50
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R@8(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 96
Coordinates: (2, 4, 0)
Direction: South
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  2 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 2
  P: 66
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s@(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 97
Coordinates: (2, 5, 0)
Direction: South
Next symbol: 6

Hidden stack:
  ...
  (0)
  (0)
  (2) [S]

Dynamic stack (15):
  4 [Top]
  4
  4
  -2
  ...

Non-zero registers:
  S: 41
  R: 2
  P: 82
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(@4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 98
Coordinates: (2, 6, 0)
Direction: South
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  6 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 2
  P: 98
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}4@3}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 99
Coordinates: (2, 6, 0)
Direction: Northwest
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  6 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 5
  P: 98
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}4@3}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 100
Coordinates: (2, 6, 0)
Direction: West
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (16):
  6 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 4
  P: 98
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}4@3}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 101
Coordinates: (1, 6, 0)
Direction: West
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (17):
  4 [Top]
  6
  4
  4
  ...

Non-zero registers:
  S: 43
  R: 4
  P: 97
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}@63}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 102
Coordinates: (1, 6, 0)
Direction: Northeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (17):
  4 [Top]
  6
  4
  4
  ...

Non-zero registers:
  S: 43
  R: 7
  P: 97
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}@63}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 103
Coordinates: (2, 5, 0)
Direction: West
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (16):
  6 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 4
  P: 82
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(@4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 104
Coordinates: (2, 5, 0)
Direction: Southwest
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (16):
  6 [Top]
  4
  4
  4
  ...

Non-zero registers:
  S: 42
  R: 3
  P: 82
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(@4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 105
Coordinates: (1, 6, 0)
Direction: Southwest
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (17):
  4 [Top]
  6
  4
  4
  ...

Non-zero registers:
  S: 43
  R: 3
  P: 97
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}@63}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 106
Coordinates: (1, 6, 0)
Direction: South
Next symbol: [

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (17):
  4 [Top]
  6
  4
  4
  ...

Non-zero registers:
  S: 43
  R: 2
  P: 97
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}@63}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 107
Coordinates: (1, 6, 0)
Direction: East
Next symbol: 6

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (17):
  4 [Top]
  6
  4
  4
  ...

Non-zero registers:
  S: 43
  P: 97
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}@63}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 108
Coordinates: (2, 6, 0)
Direction: East
Next symbol: 3

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (18):
  6 [Top]
  4
  6
  4
  ...

Non-zero registers:
  S: 44
  P: 98
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}4@3}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 109
Coordinates: (3, 6, 0)
Direction: East
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (19):
  3 [Top]
  6
  4
  6
  ...

Non-zero registers:
  S: 45
  P: 99
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}46@}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 110
Coordinates: (3, 6, 0)
Direction: Southwest
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (19):
  3 [Top]
  6
  4
  6
  ...

Non-zero registers:
  S: 45
  R: 3
  P: 99
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}46@}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 111
Coordinates: (3, 6, 0)
Direction: North
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (19):
  3 [Top]
  6
  4
  6
  ...

Non-zero registers:
  S: 45
  R: 6
  P: 99
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}46@}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 112
Coordinates: (3, 5, 0)
Direction: North
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (20):
  4 [Top]
  3
  6
  4
  ...

Non-zero registers:
  S: 46
  R: 6
  P: 83
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R@RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 113
Coordinates: (3, 5, 0)
Direction: Northwest
Next symbol: 2

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (20):
  4 [Top]
  3
  6
  4
  ...

Non-zero registers:
  S: 46
  R: 5
  P: 83
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R@RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 114
Coordinates: (2, 4, 0)
Direction: Northwest
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (21):
  2 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 5
  P: 66
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s@(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 115
Coordinates: (1, 3, 0)
Direction: South
Next symbol: s

Hidden stack:
  ...
  (0)
  (0)
  (2) [S]

Dynamic stack (20):
  4 [Top]
  3
  6
  4
  ...

Non-zero registers:
  S: 46
  R: 2
  P: 49
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#@48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 116
Coordinates: (1, 4, 0)
Direction: South
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (21):
  46 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 2
  P: 65
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#@2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 117
Coordinates: (1, 4, 0)
Direction: Southeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (21):
  46 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 1
  P: 65
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#@2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 118
Coordinates: (2, 5, 0)
Direction: North
Next symbol: 2

Hidden stack:
  ...
  (0)
  (0)
  (46) [S]

Dynamic stack (20):
  4 [Top]
  3
  6
  4
  ...

Non-zero registers:
  S: 46
  R: 46
  P: 82
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(@4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 119
Coordinates: (2, 4, 0)
Direction: North
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (21):
  2 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 46
  P: 66
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s@(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 120
Coordinates: (2, 3, 0)
Direction: North
Next symbol: =

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (22):
  4 [Top]
  2
  4
  3
  ...

Non-zero registers:
  S: 48
  R: 46
  P: 50
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R@8(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 121
Coordinates: (2, 2, 0)
Direction: West
Next symbol: 3

Hidden stack:
  ...
  (0)
  (4)
  (2) [S]

Dynamic stack (20):
  4 [Top]
  3
  6
  4
  ...

Non-zero registers:
  S: 46
  R: 44
  P: 34
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3@;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 122
Coordinates: (1, 2, 0)
Direction: West
Next symbol: {

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (21):
  3 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 44
  P: 33
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{@=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 123
Coordinates: (1, 2, 0)
Direction: Southeast
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (21):
  3 [Top]
  4
  3
  6
  ...

Non-zero registers:
  S: 47
  R: 41
  P: 33
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{@=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 124
Coordinates: (2, 3, 0)
Direction: Southeast
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (22):
  4 [Top]
  3
  4
  3
  ...

Non-zero registers:
  S: 48
  R: 41
  P: 50
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R@8(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 125
Coordinates: (2, 3, 0)
Direction: East
Next symbol: 8

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (22):
  4 [Top]
  3
  4
  3
  ...

Non-zero registers:
  S: 48
  R: 40
  P: 50
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R@8(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 126
Coordinates: (3, 3, 0)
Direction: East
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  8 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  R: 40
  P: 51
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R4@(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 127
Coordinates: (3, 3, 0)
Direction: Northeast
Next symbol: ,

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  8 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  R: 39
  P: 51
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R4@(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 128
Coordinates: (4, 2, 0)
Direction: Northeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  0 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  R: 39
  P: 36
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;@76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 129
Coordinates: (5, 1, 0)
Direction: East
Next symbol: 3

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (22):
  4 [Top]
  3
  4
  3
  ...

Non-zero registers:
  S: 48
  P: 21
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44@3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 130
Coordinates: (6, 1, 0)
Direction: East
Next symbol: {

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  3 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  P: 22
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R@{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 131
Coordinates: (6, 1, 0)
Direction: Northwest
Next symbol: [

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  3 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  R: -3
  P: 22
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R@{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 132
Coordinates: (6, 1, 0)
Direction: Southwest
Next symbol: 7

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (23):
  3 [Top]
  4
  3
  4
  ...

Non-zero registers:
  S: 49
  R: -5
  P: 22
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R@{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 133
Coordinates: (5, 2, 0)
Direction: Southwest
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (24):
  7 [Top]
  3
  4
  3
  ...

Non-zero registers:
  S: 50
  R: -5
  P: 37
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,@6:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 134
Coordinates: (5, 2, 0)
Direction: South
Next symbol: s

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (24):
  7 [Top]
  3
  4
  3
  ...

Non-zero registers:
  S: 50
  R: -6
  P: 37
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,@6:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 135
Coordinates: (5, 3, 0)
Direction: South
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (25):
  50 [Top]
  7
  3
  4
  ...

Non-zero registers:
  S: 51
  R: -6
  P: 53
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(@3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 136
Coordinates: (5, 4, 0)
Direction: South
Next symbol: S

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (26):
  69 [Top]
  50
  7
  3
  ...

Non-zero registers:
  S: 52
  R: -6
  P: 69
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}@#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 137
Coordinates: (5, 5, 0)
Direction: South
Next symbol: 9

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (43):
  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 69
  R: -6
  P: 85
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4R@4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 138
Coordinates: (5, 6, 0)
Direction: South
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: -6
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 139
Coordinates: (5, 6, 0)
Direction: Northwest
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: -3
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 140
Coordinates: (4, 5, 0)
Direction: Southeast
Next symbol: 9

Hidden stack:
  ...
  (0)
  (0)
  (9) [S]

Dynamic stack (43):
  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 69
  R: 9
  P: 84
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4@S4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 141
Coordinates: (5, 6, 0)
Direction: Southeast
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: 9
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 142
Coordinates: (5, 6, 0)
Direction: Southwest
Next symbol: )

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: 11
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 143
Coordinates: (5, 6, 0)
Direction: West
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: 12
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 144
Coordinates: (5, 6, 0)
Direction: Northeast
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (44):
  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  S: 70
  R: 15
  P: 101
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}@(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 145
Coordinates: (6, 5, 0)
Direction: Northeast
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (45):
  4 [Top]
  9
  0
  0
  ...

Non-zero registers:
  S: 71
  R: 15
  P: 86
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS@#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 146
Coordinates: (6, 5, 0)
Direction: South
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (45):
  4 [Top]
  9
  0
  0
  ...

Non-zero registers:
  S: 71
  R: 18
  P: 86
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS@#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 147
Coordinates: (6, 5, 0)
Direction: Southeast
Next symbol: r

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (45):
  4 [Top]
  9
  0
  0
  ...

Non-zero registers:
  S: 71
  R: 17
  P: 86
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS@#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 148
Coordinates: (7, 6, 0)
Direction: Southeast
Next symbol: [

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (46):
  17 [Top]
  4
  9
  0
  ...

Non-zero registers:
  S: 72
  R: 17
  P: 103
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(@#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 149
Coordinates: (7, 6, 0)
Direction: Northeast
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (46):
  17 [Top]
  4
  9
  0
  ...

Non-zero registers:
  S: 72
  R: 15
  P: 103
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(@#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 150
Coordinates: (7, 6, 0)
Direction: South
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (46):
  17 [Top]
  4
  9
  0
  ...

Non-zero registers:
  S: 72
  R: 18
  P: 103
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(@#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 151
Coordinates: (7, 6, 0)
Direction: Northwest
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (46):
  17 [Top]
  4
  9
  0
  ...

Non-zero registers:
  S: 72
  R: 21
  P: 103
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(@#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 152
Coordinates: (6, 5, 0)
Direction: Northwest
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (47):
  4 [Top]
  17
  4
  9
  ...

Non-zero registers:
  S: 73
  R: 21
  P: 86
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS@#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 153
Coordinates: (5, 4, 0)
Direction: Northwest
Next symbol: (

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (48):
  69 [Top]
  4
  17
  4
  ...

Non-zero registers:
  S: 74
  R: 21
  P: 69
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}@#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 154
Coordinates: (5, 4, 0)
Direction: West
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (48):
  69 [Top]
  4
  17
  4
  ...

Non-zero registers:
  S: 74
  R: 20
  P: 69
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}@#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 155
Coordinates: (5, 4, 0)
Direction: Northeast
Next symbol: 3

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (48):
  69 [Top]
  4
  17
  4
  ...

Non-zero registers:
  S: 74
  R: 23
  P: 69
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}@#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 156
Coordinates: (6, 3, 0)
Direction: Northeast
Next symbol: :

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (49):
  3 [Top]
  69
  4
  17
  ...

Non-zero registers:
  S: 75
  R: 23
  P: 54
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s@#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 157
Coordinates: (7, 2, 0)
Direction: Northeast
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (49):
  69 [Top]
  3
  4
  17
  ...

Non-zero registers:
  S: 75
  R: 23
  P: 39
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76@s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 158
Coordinates: (7, 2, 0)
Direction: Southeast
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (49):
  69 [Top]
  3
  4
  17
  ...

Non-zero registers:
  S: 75
  R: 25
  P: 39
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76@s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 159
Coordinates: (8, 3, 0)
Direction: Southeast
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (50):
  4 [Top]
  69
  3
  4
  ...

Non-zero registers:
  S: 76
  R: 25
  P: 56
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#@.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 160
Coordinates: (9, 4, 0)
Direction: Southeast
Next symbol: p

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (51):
  4 [Top]
  4
  69
  3
  ...

Non-zero registers:
  S: 77
  R: 25
  P: 73
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#@)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 161
Coordinates: (10, 5, 0)
Direction: Southeast
Next symbol: 4

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (52):
  90 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 25
  P: 90
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#@2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 162
Coordinates: (11, 6, 0)
Direction: Southeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (53):
  4 [Top]
  90
  4
  4
  ...

Non-zero registers:
  S: 79
  R: 25
  P: 107
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<@8{{)
([}#)}]}[#P]RRP#

---

Step count: 163
Coordinates: (12, 7, 0)
Direction: West
Next symbol: ]

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (52):
  90 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 4
  P: 124
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]@RP#

---

Step count: 164
Coordinates: (12, 7, 0)
Direction: North
Next symbol: 8

Hidden stack:
  ...
  (0)
  (0)
  (4) [S]

Dynamic stack (52):
  90 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 6
  P: 124
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]@RP#

---

Step count: 165
Coordinates: (12, 6, 0)
Direction: North
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (53):
  8 [Top]
  90
  4
  4
  ...

Non-zero registers:
  S: 79
  R: 6
  P: 108
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<4@{{)
([}#)}]}[#P]RRP#

---

Step count: 166
Coordinates: (12, 6, 0)
Direction: Southeast
Next symbol: R

Hidden stack:
  ...
  (0)
  (0)
  (0) [S]

Dynamic stack (53):
  8 [Top]
  90
  4
  4
  ...

Non-zero registers:
  S: 79
  R: 9
  P: 108
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<4@{{)
([}#)}]}[#P]RRP#

---

Step count: 167
Coordinates: (13, 7, 0)
Direction: East
Next symbol: P

Hidden stack:
  ...
  (0)
  (0)
  (8) [S]

Dynamic stack (52):
  90 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 8
  P: 125
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]R@P#

---

Step count: 168
Coordinates: (10, 5, 0)
Direction: East
Next symbol: 2

Hidden stack:
  ...
  (0)
  (8)
  (90) [S]

Dynamic stack (51):
  4 [Top]
  4
  69
  3
  ...

Non-zero registers:
  S: 77
  R: 8
  P: 90
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#@2};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 169
Coordinates: (11, 5, 0)
Direction: East
Next symbol: }

Hidden stack:
  ...
  (0)
  (0)
  (8) [S]

Dynamic stack (52):
  2 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 8
  P: 91
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p@};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 170
Coordinates: (11, 5, 0)
Direction: Southwest
Next symbol: <

Hidden stack:
  ...
  (0)
  (0)
  (8) [S]

Dynamic stack (52):
  2 [Top]
  4
  4
  69
  ...

Non-zero registers:
  S: 78
  R: 11
  P: 91
  J: 86
  F: 9
  A: 5

##]##[###=p)R={{
#[r44R3{]3.5]73{
{3=;,76:s7639,;[
#R48(s3#4.:)R5r(
#s2(}p#}#4)p#{9{
#(R4RS4#}#p@};=)
}463}9(r#:<48{{)
([}#)}]}[#P]RRP#

---

Step count: 171
```
{% endraw %}

You leave the example dungeon after 171 steps.
