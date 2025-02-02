# Chapter 8: Cornucopia

You have entered the seventh dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnome sits on the bottom stair, sipping from a flask of mushroom brew. As he looks up at you, then down at the purse of stacking on your belt, you recognize him as the cartographer from the first dungeon. He leans forward, as if about to speak. With a magic marker and a flick of the wrist, he scribbles a line of credit onto your purse, in the shape of register S. He pauses for a moment, then sits back, taking another sip.

The stack consists of three consecutive regions of persistent slots, indexed from zero. At the bottom is the fixed stack, with registers A through Z, indexed 0 through 25. Above that is the dynamic stack, indexed from 26 (inclusive) to the current stack size (exclusive). At the top is the hidden stack, indexed from the current stack size (inclusive) to the stack limit (exclusive). Numbers in hidden slots are still retained. All slots are initially zero.

The stack is invalid if the stack size is less than 26, which is called stack underflow, or greater than the stack limit, called stack overflow.

Register S serves as both stack size and stack pointer. It always points to the slot just above the top of the stack. Initially, register S points to slot 26, indicating that the dynamic stack is empty. Pushing writes a number to slot S, then increments S. Popping decrements S, then reads a number from slot S. While popping in effect hides slot S, the number in it is still retained.

With plenty of challenges ahead, you consult the map:

```
#}=}[({[{R[=]#)#]#}R}RI][))=][#){})]}#){R]](#[fRR=)}R}#R[{}{#]{{
(7}Vn].5j9N;shh3Tqbw5bx05u*aWQGN4*)T}7,x3}h2vf23eaYfQm;3)4M};>*#
(9aM(z]20L>wOv6W;%zuI0R)n;r%t;>W2bw6d9>oOdW7)wi1)6zOXFcAE}.j8F-[
}}[*vok%V7mnm;>5j;KjYGJYEV(9eHI{jpmn96>#*((on26d4pRjva4FTZ+=admR
(6O=b.g,gqr9Yom,;Kq+mDbXOICJ9OpUTNy>W]tdpRQNv}p=I2}IV[cE[+E]>=9(
=#pE]j9Kdy7miKc;6vj>lbYfYD%Cf.63JJVdcgoh>XJ[#PvBa]y*avhD%ZFwQK-]
=Zm9:tnK>4>Eh,c2YWe,YxYY/D=R1cEv3I2hP=OkA1Iq##ltRR#UUG)d#[s(h#1#
(O<okNL.]dl2kg:DeEsa}b*wJ++%cyx=vTr#X%Dl=+P*bQ=K+xeH5-9G,YOIoTD=
RY1eYO>nWf.Zrlv/lR,,d=2la{)x4]8%j>>cRKq.2x,EAY=6=6X]d.pf{Ss*wzBX
V:3;VdZ,0M1zKJYRf7{x=T[GX=wj[+4joCVazx2R[1}dR[kA({qn5_wYH[V#Khm]
[x)2w+xHRH3B:eiGuaM6QBn6qF93{ahcH]G]ysWI)rAKUrl*AN9noaEItmsRc6c)
{R7lH2[dfx)K(-w1q)MV=,{awwjq;}Rv-{+%bVFogkGoUZt=Y}NJU=[y#Fg+Q[h}
[Hm7-2v[/We,x{G3CfCl3QT}U.*xk2=+Vnzrh(IceoUc0H%zi:;rQs4Q>Xr(r8B{
Rq8HcO6w[WKT]]VgK4nF.H[]ABa6c8nHs%XV408h8tLXR90(deOsZ3XQ=,=.Fk>}
#d)6HvhR>K]+,.34W:dX5Na-3=9bD)gWMp=)x:HiL+#z#{(C}lLxl.}W:*=*mC;#
{4yDj=HiqC]}5:{#Zt8on(:k#:Z(/A>6]j;3sB-+opW,*eTiOnRd71+ID.Rffo({
{7]OIJ/2daLjIjyk+11=>.+/75ml:E0{%Ews0+X-)-CC#T22YCoUBy)FiL#ex#))
]ebaa2ZD=K{]7=cZ+LBweR]#O90#F2DI]FK4>D*f,(Gu4(i}x]E8LiR7UIQeY=j)
VtoORHjsVy%YZlcsyT72dC(..+*#M#k(,Q}a+Oq4RoN/-j}xB=+Y7-:.>L]L(p:]
=3D#l[5{(mdgk1)Db-,>n5w0/iexkA(ng0M5ge0xg(],F+dJ5.4RMiQ3HlcqQid]
#]y62:#{qntaNrq>=suRybgRb/yVs;NV2Hn7UutE5smgYK*k=kB#f[}ZO3h/J)e}
#8R06JK}n[#vW)=0;=yud=(L4t4J;X-Oc+G9jc:=}vh[Ox[mp#>Zw]Zz#uDwTME(
{g(Lt7=#K5-lmgZ/}f3x4l0wY}Fdbl6)DZ/Q>aHx+i*bIR[0RJre=)FDoLz,rNx[
)NgZ7r#hsB#(D9e*{lk}n-KgoQUoN(eg0;-p{8N#oE+p()5Qx=+]K:(O(o-GZZ]#
{M#]mr##>#*{J])78{-qv>EOFTW,Ka[U8{qlU>o[]T}W1Gr]FuoJ3=apR/(v1tj#
)Gg#{:14x3zJw4Rp)Zsbr=q2Uc5oEywmhEUTxa*fH])QcZ8U[UuMKLA%X4HrAe{R
]=M9oAv{[[/OA6E102i/Ki,mCH[BANvDU]KH(up8F3vn.]dR{N=)f>>/]6>X]lI#
#u#(ua9)#5nr3/#X]NZ(U)JgKJr)1Y)sD{>2(Nz:fsZ#9aR%[+R5}IcCVrT5uw-[
(NMM7I(57#+]Z)ibpzdVb9OZ20*%TXyBQU9KO%C+g2;(f2Rco85n1:(,+K>B[#{#
[mmN}q+/YkM7]H#.H#u-(;}uz.apXG71>%TR37eX)LR7H{+]p+pQf>>}}Ri.#]#}
#g+P(evWruUCrXUx;]74*a5xR2:(*=6O{Q8+7J*[(MdR(Cbw+=YOUxUQZzoXO43)
#RC>}((=(R](}[})RhwR8{)]##[[{(((=}{#{]##])#R({(>i>O=]>.CYpXRR]]]

]#}R]{(#()}[}{=(##{}[)[RR({)P]}}}[#)}#[]#){=#R#[(()}#[}[#{{P{#]]
#h{0lkyL(ykRnH6NFRPun8a;1T/V9ioftl8kqyv,I7niDMwk9Omws:=3b.QVL<Q(
#bVK=(R5wH<me[wB((6nB%}J#wVV4D<FihuQvA<)LViu#p#w7)C+C5V[{W;G/du]
#1)LgI[8*lzel]<H=q[U#Z3>R)C0#aEQFW##N5<Vt>p(4pu=0)z;%FxJ75uRI#d#
#RM4k}ifR5i>]v0]0u7=0AjZ,V2GIJcq-t)<xEV6N-O.Z-IWO[>(XbJ.m)au<ed[
}I4vcDsV.](EuyIotie<rI7J3IJ=LTgeCg}>.yxh<F8:=t##{]DR+hYhH5/aF;I(
{f0DcQgj<p<k.TAAI)gnJfyD%M*fapq0gA#ax67l{.oqBU[6O1KFJGECBZ8mhW5=
{OhMi>>,=Rju9Dl.G*IHDAa-LO.z]]U7#1R=/#p#}}>Tzy2h#]T(]{v20>dGRlh>
(j)pE><7yu}uOx8C,,N;]B))]M)m#3YOB<<o(Kdv{971,sstw%fHsoxR>2XuUqO{
{k[Os[LUXWaJxmZkyX08]fRe]dga,yv.aZV>Y+x8%}H[>c#,(>K;t=O=Inyw[)*o
)},qn5(.]7c2xG7AwQ}}](+A2gIMYB=E#p>n=}7c.5w2MoZ=O;wu%%%{=)a3;}ue
#eFfZ>8q)qh2ae+*%X.74R*t={#0#Rthuvwq,cEWrL*2/}eeyUHEP4iN4qYJ0YM>
#}B%O+{X)5iEY2(hWeXFV8E6RU#s##BF>#G5Kp)R3iU0Jj9Tz/zE*=4j<h/+qi+[
(6z,8;X}Bb0[hZf1AevFRE;lWT>Y##3v{fXVg08yCUZM0.2dwitHw;DRZhcubR<}
[NHN%=%E<oXg)x>U+d4V2ohGD1,bZ.I>Ul[E;mKVRVznIu+y-=Z#>(-ZfzC*yl8[
}MUg9z>ECM0#2{0Om)kb1*Wd+a=yd#<u7g9hm.zrl3]zr1Ts+Z;Ht;>6rs]WH[a#
):r4iuCg7LJm4I:j>tTo<,d.0WQ:ln{V*aZdQ.iHdtMn3F5mF4tGj9=%3rhuiYh[
)t]4,o{4>W,DuH[M>iV+X5;twYIgx=Gl,{(*<da}Y1iDVM6A,={AfVCOZ=;X8(9(
=y-*NEsQ4}V,ewRAqh,J7sGIbVqlas4Ge8ZCqUR[cCA*LXejRs/vZ+vE<z[yaTk#
Hry)I=.arva3=R3NDli<9bSDjp;ipU2H[ERDVqd3Vlx9nBZ%mQ:Rl}geIV0gHBR]
n(ToW)we)]=F3m=<mrM3bpj7evR:]e7bm[ct4YYRCRtBOZLhtc;Ci5y26:k9=[o{
c=Eu(M]V;iAzlA9bX90lon3/DZcZ+A*E=LA>k+cr-a3ILSn;s=<#WR:>Rj#nx6((
XCiQB_2ygD6ijAjMsLwO)*}tdolac=X/6lzD<B0wLRC#c:IQ*a>}gr2#nA%7c(;#
[7/e7-x3pWlAfTjL8qJYQ8H=A=;f#==iX08qLDv%cWe]RvcytUn/ou3:}Xp=R(Z[
#k[v}LMg<}B-)6=,aMR+5<.Fd[.rE>;vnCm,f<F(2LwSBV#jXZ=p](6Mv=Tf4Cd#
(s;2yAt>l(mTLk9}r9(xYiMBgC)9dL-K45>rBMG>,X==i(#}NGV{Dl)0K>vK:%;[
(Hl3;%HT5Ag:mij+CtRlo:[hH.kfIOi-J)1eKv1(l_>5%m+e9cq0{<<(:Y<Uz:[}
[9%3C[OyAvaGIc*,eJbYp6VM)XRn0[,Q=*<W[))o}=W=G>E23>J}RoJ(T%cK9gF{
)qQt#m1Dx6A2]#j6Z#Ih(H}yRL+H{FR}y9o2jXivmVokC%3z-LvnKvlF4p<o(=x{
=Nv4yz2ywI7Y-ieBhXLkcAU-ts1IGl3=<zF59aZ7.(#{##(({#}=i<<]h=hXy*o}
Rk[i(]Q:=yRSeDc}HT)9[tW4J4[:+RbkCr4D6XABoOJGCF./LU+vq2ITf.xUfan=
{_}<wm{[)[}##)[={]R[}(]{[#=(([}9sj6MH8TTDzyxV5a<><,mM<{RRm{=}})_

#{R5}[(###]}}#{7wa%cK=#[N+HK1uK9q-,>U=6){[}{({{#=b8}{JR:0=[(=*})
{c;>{a###{AFQRqLzZAQ)#+#z}})){F.n=>FgD6*76skz(I4=z7ZUWqIQj=>/m>}
)Ex+G/3/Uoq=xt%RQL0s:RrU1DI:1gZ;mkJ8F>[5h}#KYY#Zm{=U9v0F=w>2H={#
[5qt{Q%9Wun.vBU,oZtVhuw<LiMz##]ERc2*U{szC<+emO4g*G4>zH[q=Yy2=,H#
#.h%OgGp[*h<;Uezo*wfzDqpyphrs]UD{l>{8Ja=sOv8}2QrGZ<8p=idGRJnZmE]
)7No6CdWrn2[)-#rjs#>l>}Fi=hOJDl.t}9<*3V)h/o=q(T,tUid7cuH}UZz]))>
pwwd#9b[T29e[f}cv#VJz7R0-5J3CQEkK6R(5#E9r7y0=%nQa#[)b]h]2{m{h##*
G7BVQ<<T=>CA]KMX)W]Cn7OaQ}DD6C>m#z=4W=:jsa<5EWq5e.0GA:]u[<}Z#]]<
3>m*d<kYcGi2q;v[%#D(Y7u}8]In+YhclE*Z%c/55,mV2wU.tDd/,lBN<DA1e;%]
sr8Q#{G#W)9)o2RhNI=A#*G=Jj#LK[+,eOV<G2XM=mD)<Fd=N<m)hg#xi2oQ]bd[
rR0cCTnRaJ8)#oj/2[r4FAh#;##u5%D5%h<];}>R(1HKq(7H2-;_nz#(p[2ZR]W(
B;9Z{<79A).nWcrf4XuRlZA8fX:j=wA=K=d>6A7=x:bVfeQBL)awIbk/gZu7l)[<
h0Ra[5=/hI9I;5}-xwRV+l.#d(64Ez1,<;[+D#oLJ)D>:Ve.WZ.9RH[#y.v]c0#-
p.*;]{n)O>5#Y,##dCC%R>,2/6<p(R.1aT2yh%r670l=)=HA15vxzl(aEV/KJ%]H
8ftP{;Loj*VEQz<bF2VMnyS#,]t8{#><NlQy;FbToM=%QMs9;C%N<NFCGMpZTK(i
DyGskN<%GW6YMG;V5KfTh.YsZ>CLJ32h)M)xJ2ozp:a}xTM2Nf#zEB<hIO4T)6#e
:{iXjRblfruA;3K2<NCU7iELp{q9.==QOw;Xmj+Vvr.jgrqkuWIZGT*W6/=yTL>V
9]E+#xm#<(4j.3Ir<>r*h:i5LVy4IR4M6Cf({3NJy[}vpXosU(oC]R6wzBm]n)}g
=R-t[L,B0u877d%)ftH]/]:3m%vl+#>(NCW#+{a.(YOeuuL/xM/fa4nW+e1Tv9Z>
RYVW>RtMoX;9L]YX1{v+s*x-H[8xe9E=ZqM*C}5*8YsWR{eexWZR;j%#%lM=J62}
]1e#{h5[[Kob/ac#s(5]g={25x[0mvWmiVV}Rw>0f(Nkej)hpG);#[m42QX6f57#
)YbqGwNZ%d+=K9W6XHF1sF[Z/y+G,Q=n#mV<P{a.R28z>7ElgaosVzi<0tI74#c(
(qEOurHLH%:jmtemT*uoklaF4..,[JB=TuD.+>R7Wwo)fUqN{{<>>;*cs9wY=uLR
](4#ZEjui)AFa)Dlc,*y]}E9[8}um[/Xx2o8at*Wk8Lt0%5c}(2#m[fIJvA39Bnv
=lz%(NCNC8B(ppGl5qF[{ZN)Ea}}1</o/yl{m#g}v].p;kTea9Z>wgoZuKATY2#B
)%eW-4N<;b>xMg2g42-Dn%>kjzQ6hR+zC:<l=Dj<nJz9Nd>FDrsYON:V:<}WXv=l
(#y64Ky]yqVdLCMKYVnj=Mf)R7i+NX8fB:F2mp.Hun<n6Mn>tl(02AsscVAhiBa)
=z-=0L;{sF>l.:pEBkT[fnF=Uo,cKZGjvq2EiD[NAvv/)<4:[<Bb6U.mf=yy429{
*{ZY[c[{1UHXDLp>KgTFbg;.Xf04c]/RUzmJpZTdDk,-dIj7ItAfk>rvm+}7t8[=
>}*V-akxoO[clO(={0cY=v]{#4*O%V+##mZ{vaB}g;Z8)sc)r=#*2{;VX;4jWpZ[
]#;[#][q=r9tz>U7>qGQ*xr8fze+9Zrekq+K;,rYm7V]):=Hls9*[yWb[zTo#]Q(
),DLN>]##[#[[[}({]}[R=EQ/={}}]}R#{=+R)]]{P)ed*tA<)EUJJ=[)}##{##(

#(>}}}(}](}=R#=Rql3R#{{RoW}[R)]#R)=<T*ZTcK6I/F9CaFe*HkO:7hmkuu=(
[C7<=0HD{%lff2]*pnZ-yuMHo:j=jg,NOq<R#[#]{>#{#[({[}[LuER.u=_<_)<M
R5W+ygeHW,aKgQsJTDUBzlirzuF=fQ,o-dKN[<sVME+(RZ*t7oQqtZLR}s<z/4:;
#x:#yw9>N:#mmDxheww)0}-5MEKR8]2rd#);}G[I.Rscd6e}tB(<29)4f6BgHy]u
#D=*DBTbH]{Xu{#z(wY0r8*R#W9[BV6#u(<#E/0)di:y(dB;T#:w)]%WHAUn[/=e
{o8qN}4W;0O/-=m#i[><4<yGJK.9euj{uR#u-mRdBF>IdzZ,=RnW}F.cLFoQ)v(<
)rM{yIbTLUbN44C>IF5j[u9:NY+B7p-fe]+W{[m:cZgBJWkfD9yt7Rd+gn(4:[[#
OZ#guWtoc<M01)>.X;z_8)F](}g4MS<f]339R+0-70LXMcWp,)Ay3kRw{UtM8=>#
=<{wmRiDX;qC5k>qkTEvRt9RY%[/g%H[mH,d>;36u7N.6}Jypf0Uoy.4Hv7GB70(
{Mq8l[v1R*Im1}}3o-8#1#j}s}>Xr]VLJfidnAz.8waOg:a];]Fgd)Ug0Y[k,]e]
=iWr=A),6J}8va[zpdWLbtnf>3#9t7MCRK8}j)<YYvICD)h#-di0h>RJ]fuM}Ot[
[Uy(g[sx}wBR6bv=X%8io#%H-3/+=F=E:]R<KUrQ6-[fp)tJJGWznMKFFKquF0k(
]GXLw%}[0yoA8Z,ol*js1uyw)DltvH1tD2En6/eh7tr<B]JXYy{q;QIlM,L%#y>[
[1W};2#,H<b]*)ujAnFE:<Ngvy59UyT2dA;kCLsy/EB]hutNjVAk+RNp.OMbIl7=
]:m7;oReu[,mS8#ciu{R*igB(8MUC]<:z2(G>>}Ts)d4)x[6C[cV:=y;ui:[Ox+#
{D8#5#{o7pEI==A)I1a6[lzNw<YZ1#B=e4Ycg#-Scukfm/q}1w)rL[gVBbR07U9{
Ro.+ZgIAcDUhU8:s+WslsDu/G4HNFhZly2[f]Md%08}>(G#[A2-6A(*eZpNF{B<[
R0W55WU1eO8e9d%W+<[=u.)kbZ{>fax]6>}q+bD}a=1{CO{E[E-z6f=nl]Y)}Y)}
Rlu[R##m#-l}[wFZuK8#e6U(nc9=Y)<{=95bxkhOBl,=d[yB>*-RoMT06y,LDdR<
oEI9<}:#,dV(eQVdg-0,wbOErsEpTNXmdQJy5[j#U5l]p(j%)sM)iapwjTzv{dd:
Tlrt/*#3%jqW#q(rXRF9K.f5Ou0]>k(T3zo5JQ<77:}*4AftfCFex-(2y>UUI%vc
(.TM%hRN##d##}ou{1HW-N*0v1}g7j]h::.;2Ts2Y5/x<-;F4lD(R#QG3}pbC(]-
}5qW8h-V#;25=;yJ4sT{o0B2}}(Fiu5Y=B)Lj<N}#T]f[gO30Da<<Rhsq:eh68(Q
)iE2/L,sd89gG*7RAF*GTO5He1l=r[GcjOO*W#%h(j]sFeno5>cM#gt{5pup=k]j
M1w},#+]X#y,,J7}B9aTq0{yMCNg/.fBM8Bd{R3pxTG*{+3M3K8<vC,MOy;d={[j
RcyLQ[7M[j<(oZV.xIaY;K<hyu(96cp(bC{w(o2Zf6Rx7h<y4FaFDcuIu-NHqO>Z
ri=t%9ft>nE24v>]3RbwTXxW[vM4K%m6hp:){aUI#;w=8wN<#mx>OQw}siJY{e#h
,eEa;#DM>(<xKsiWRe,##4vvj#qgf_mC#myJ,Kn/*mp-c;lzr/Wv:=x.=}>c})=.
RFJYl;37lUe,c(K<u46BBON%Z+(a0AYrR->B3{{W]6Rk0.lkR]av1<7c8>l(5d)0
<(h#[R([#R=)}_n={JT2/XsrCD-R[R+jL{9#}=goqjnl0aAJ7vGGA-dx5RD1fi:=
9I>+YTAE-IthC<4%<J-opGsrM7p>.AzJcXEeCq)[hIEN}F:zj4iU*n;{G6Ya(Wt}
((#)(<K5ccu4H>[###]{#{##(}[{{}))Rvs[{{}#}])#][)R]]R#]R)({]{]}##}

{=<[()=]#P##}](]####}}{X4=#]=R)[##[}[#{{[{}]{]}{MR(#_]#=)[[#{#]{
)E(rK#voq{}%k0XA8Bw7aAZ47fc+--wcZN)BZQ}xU<#)v>>eVH4XuGyeeLE4085=
#.99}-*U##7X-qgR8gl(=4k[#x#YQZ#DREIEHtX/yOMu*wJY>[/mq95u2v(ZD%N{
#Rg#W{:<1[n-O(/{*j0YQt]WlalE7d}KJf]h>[xQ6dt:xo6iR}Mam=rjM8}[-fb}
RKO+J73GNp4KC>,/D)}##o(u)zc7tGIrfmm+hIt>:C=N>YZKVnFJ25jOc631fTg(
[xjTQl2G;wIG)I-z:/<DyZ;Q)GZa3f>X0]BNrBY)rO<=wv}iu(E#>pZ5::>K[>lB
}{{(chy/RTc3o{r<4F}+VgCcn3}ZhE+=#9{kWWN[q}om/C#qRbChI0//pIJMc)b2
U#loH*YHWqR3Bt<N)r}wWAl/Iu{Nk[15;[0NnbjrB-BGrJZ2=KC[}tWIh[NNy[<z
ihIIWF[v,wV.>9<#7A#rCoxc(=6t/KyUHDGf<V3HnR1R:RXf)u21Qg*Ou,J7=ftR
e*zUD3#z2[]a*#f#}jm{viiR#0<0+z)[4tDk9MXBM}x#Z*NxG5HKeH+#%nA*1#=)
=qNj.ZBcAMBu:,OX/-IL=pxV<5w;WgaO4e72-4iwAo*lo(>)+8/RB<R8DD.)1]l=
}(kstqud##C([#,1i7#]=%tT)GYnl>bycH-NyEQeV>G+xLWJ*>z{#nR[7za2;LD=
)Ub>pA=J{=2WNXNhmM{]gHO0Vni,(D]Xjw=v1ii%tk4QoR}NUJZ]xQ+2vQeH,q<)
(KlCRu(/(K=R.#[3eWPgR-EO3TWY-Xjjxj;R6ge(UCGG#oz>cLmD7.7ba,R{Fit{
=2)}ehR2G:HKN+1+zBq)[//y)Ql3[;09(Rv=<<Ke{Be+>0rQc=m[]9R#7{l%wmh)
(V#6TrI7=5wW(MMpK}+tH5H[-Gj3CZMgEZ}49MTF,xpvGuye8INAtu0:66exp=Q}
}}C>E(yW.Ni7+GF7Rv#vWz=(s,#Orq](58(IR6[4l)}<0rf)RGoIZ{[-[(f1*E{=
}Y5Jbe7enk8Da0c19}kF:c1DT}8<b>y=R<tvSjk[mtC]w;HFBqGV(3[:Ke/X*)l]
}v,G>(-E8hT:n{D))816nRFZ{OQO*ijLCa>Ese)9{%5[,[=O<=9p-:K#=6A[t>3(
}%a:jtp/k6yq*>XY=Vo#T6CbJ#AF9ho>VHlgkWl11Tlsl0bEHh:zp%,EN9Ne*+R)
}6xwwAYsdpUl{..}>BIaoG[AR.7d<a[cArplEl)6R9DFpVY:CIp#j[{k2<l:49J}
[fiKq1I=DKpZhT:,D-QJfn*kJDx/::a{fwv#bVc=Ay(*//ysk;26yLYa+Rp#Xd#[
_6Aj]y]Esu])OQ*cK=3}2dRop*]X0+TZ%ZvT/d;=).;p>61H+Z85.4RO1L/W4#;#
[oeDTKKELAE;k}Lp2c[kzmAgibQ>+O[7Ugl8x%=CXe-itKy{#<hy1,LNKq9xRY##
}A}DZ+08#4KRAy[K*E46#+>e#%VhH#b4,vNd,,])f;{0y=8#{ngMswEg2OqfHQH_
)))AMh2}2.IAuub;,[9F>0k)9}EKuLq3}qEeLcz4Y4lyfrH3dRFq]1d[qVq1Z[<]
#9Ghxl5W<X[U(-<]BKRwe(0=(NQ},DvR]rsRjbVpEMiu>1Tfijg<#:#iF#g#,)L#
#+z(DzRN<jDUpn(F3y:yd}i[v:2k5q4wu=UU)RX*j[b)Fzv6+dAMXg>ko1<;)===
[,>N(A{(+e*C2#/N)BcxlRE}eCUNpyn:2t<.aKOovrq/m{(oX8FQ=-;##<s.J,Y]
[f={be0_kc[e=WD8iOaqZ=mY=].)Uf},=Y=wz.BJR0,KFfxo+[5Gj8{##OsKE==(
]G<5CV(cuUttYj+({(}(jE=fJbG<L,N0LjnC{m}L[DEl[tTLwgE6bdBtpDfulAK)
[}=#}#(}=(}]{<C9Zpv3R=#R=R{#{}R(RZ{{)[=)YpRf={###})]#{#RXr({])][

]{)R[C%=]}(}{#{(}}}({{]{{{###{}[R]##){#R-7m}[(R)}[)]}(##P{qZu%v=
)a3lmcUocxcxzD6(JbCf)VIeE8{r2TjNO4rz*Ya8IWi9e<<s80.7)ros-6tno*GR
]#7k:;]r)MYpGE}M+8Kzry4hLp+B8C(;r0q#v{qE(,9#.#4T<NYTM;GUMoOy;}(#
#m1]r:>e={Z;aIU>mTDhs[9}*Uqr]A52cw-1<7)j:pII]fuI7BkEGy{#==HX9Jf}
_}M7Rvwcj)[f9<tjawbInI;FzL;B>hfkdV%rpj}<Zvv9<:IZqKocxc{F=R.>{oY#
[eHVqs4dBdUNN1D7=E{[koc[Vuv)eu<VmeMcBiCXGexY4Wk9G=vr<(5=OM<39<>{
=E1=k);q*X{1.C9Fls#:Rir}2d>o%4=Np#>5YU7+3}t/#]Q=4eGetmXoVha;_uGB
=B=NRG;9KWN7k[O09VEE:B%ZV}*v}sF/yEq#oa=+-w/2UChVEV0AZx9v24T=0>:R
PEv[f0Bf%JTg<>Jk+l15i)I8LD##f4b21)1(}X/+wabTTb(:/Y:T#w;.-U[h(.2]
[f#Z}mgxuOgZyKyzU78x+-rvrU8Z8kd*-g%VfpyGI*kU(]HBJ>>mDt9Jf2>]yLa(
]FL#n[2vJ+%3gD#,l/m{/K(X[hxWRUc9cba]kNyTwbHB4#<M]X#Q}Rkn#4EXc{;r
Rkf#F9}iVWy5/:o{h*vQfbF#JW9fo<R1BBHEmADlj<qrI2lN;<;{}K(}[z%3Cl8.
Qcx<u(ZmnoW:k.n>:w>m)LmJvu=eT4,NI#kKK#(L#}uShy;RjY,Vv*VYm>=7p*Ae
RL4WfCxWmu5CVd:1}d.Nrtmy6>f{+zAIft(D-d#+[R-#)s}<h-ualb#Z1z)oZGrr
)Oxw+b##eXm5e{.kaLrtok8#ho%,qOD),9x]fhaBqVzq<io=7Ju)Rco6ytBH,,y=
=C]]jQ:wVvmbeOLfJY=J%tdeq)1Asa0:Mm.{{=oRQ}e8*5]Op4]k2NFxYjT#e#H}
]6c<)#OI#,,++Qd%=8Q[%mVL8zRHO{DIoWyMLc0Rg{JR)a-xdG.{Tt(GQV#o>:c]
)jq%E*5,dB,NjLIMe/x+JgRA4Rli%<nk8:WRdF#>5*-QN-fJOq}0[-Ynk8YN=)T)
}2#1<DYg2b68oKtT>Dnck}3zMBU]oHDm)H<6;gs)=Bs#{{L[-#i}5.=M=cC##<T}
#])O6WJN#a6gZ<e=]pOA9T5%3w,8XcI<i}W+jNDsR1yvZ85cX-Vo+MzIvQYL-D%#
R#;O[QZ5x#v4T+nf<)b:OwirCgK]LxId7#>IXw#f*F-=m}v#wvoQ0(j3/.(>==1}
[nf)0jI:n#jDO{,nq,-(QB%Mk=.4EjO*wlmIjyl4[K::5ddfZnNnhN]crW>sY)q#
],FU*#Q)n0ai#CzQjQ%G+Km7a#[{O52{5;;)28PeeLz5<]Ln5%%4oN>iqX)ch=H)
({dDc4kxiZYJw20H/+k8,endW%B</g3=W+nVqce]e6BIAsl)d];IKY]=0Ezi>=I=
}cB3:P*HZfAL([:X(L[-6]<),loe2ZDbid,-dvuj;.=]9Ig9c;7aH}:k;c3krlk{
)5>,Vbud)(lL[wy5Q9iw<h#4W[rH*MhaI(DFlBy.qvn8VU[-F=Rvedzi,g}09HR}
=3XWwpI-Qkz([V8HuX+RCe,=Y2TaZ%:0,}(iBtd=)7O}<]FQI{87dTn}V;rhmYu[
{M{##a4RoRh*OQ{txdLz4/;4bdOeZe7W,2CMZn:jBI+W*E{pR/IyBm<=(w]Uqm.(
)n<BK,nb9D>GxCO%72ssAQpLcd9)0gsv=uaY%=1MK{gw%#]UZ#b*DU#l}.>[xt9{
RX)G#.)m7(t0KuqAElH/./+n4}JwofBuC}7z=ig2%d#7,Z[9Fd}EhiTDx8y5er-{
)>0:Dx2FM.(t#[)O]c=;zp}X>>;[:Qn2{#(=y37xR+1iOeiLNRapu7zAl1ztZC*]
#],R#(=}RT{R:F9=[(](({R]R[#[}}=)1:TIE=}{(_][R(}(]}[)[{})#}##R[}#

]}}[v>#{##[#[#[([[})}##=}#=#R#})[{}P{[)Ru74*)}{R]]#}#]}R##}(}()[
#JA4FNCvXEJ1]x}3i)>:XWcAnxMp](ArJxu]blRlRf8}=b6DJpKDoijyU]#0)fr]
_+V6MRL33-tH,l;Y(}QT#VR)G5lgF8Bm()chN}Dk}N(xCn,[L>JWZ(o8Go6J+y3=
(XOEY.<UcCWr3))<UD73BM:3m>N,XWRxeml:RVm6d-,4ua/[jnRwb}o;nr]p#]*8
{*V]:E)>+uiT-j4d:+u5QZl90f,s<[y8#y0*-9*+(s:CRH96{h>Q#QaWnt(<H]/1
(>4eJ13HN8Rjd#F##lJt#V7ji/heaN,=B3(-TR7+Dvw8>QxArwj=[mpbg+2KyR<L
(BhX2>H=W{%gFM#*#8dR-#l2op<W6V#i(Q<R3q=Y7N6ybKm7]]7X68xN.E)r;#va
=5dG%T/.{RB+t]l#++(r#m#=hgGxI}hZ6yab[OQ[[#L#Nd)A7sG2TIv0GwBgE<>;
{NVrlw[cv5kdV<-a61(Y[o=;a6Ku}cRd)r}o6o34Sy[4#h#orH}9Cjm(57B=)%#}
{>emH#V2:YFgY7kY7#}0;RxG=r:}:,>{C(.mu{nis=0#8L#[U<<=xg%7uw<#}Q6(
(DF0ec7TsQcOD4J1rv84DE7FkbGV>6Qt2d}E}}]H7Ij.):{tVwQ)Qzc(m;u2#o#R
Pv4[*=;{>,L{Maj(%]HW%7eM)+06h#tZZ8,Wf[1]yO8CJ6QNO}L0:n-DcxOhDrL]
[oO{{by-WO}>Ah#<nD<sx)4Y[MI}gpDxFJbDaIk4B)jG{q}:izb;81t2%<,4-]o#
]5577-hRe*KA.PU%M5xmJdDGO<B[QY*=>LsCmxK{A9*(kUIDZRwc3Xj#8Im}qnr=
}kr[YJr:{Ni>qaF%269(Zz(nzl([1:C(+7NT4Hc}Q+}c#h(z%Ir[yx5X/dFU5pwc
=Ee+MzEW856W9h0CdHKKGzXkqgMZe)MkPu}05*XIRuoVC6app],*4L%aa,:iEl,m
x0tI}m:Z.=zgyZ.kF}(=mtc)49ee=su5nV{Gb)4XGoLI8J+86;c8VT0DvRU[<Dx]
F}Y>zeD5+l)/5;Drd;M-}pB:#C2[#niR3*]pXZB<7cURr%aOk{EJHT2#na8#blm#
L)ilBJq=b6-8v5N><QZ#R#.HZlHW{%B==Aig#3L{pK.(QQdnmr>=9o]zL4#R8C+=
Q[.4XGmkt+D0mXi4w>scW)C-k(iR)u}Czj]1=obK*OiNH2B4z70iliODqtfOt*a)
:{C}cvDcKTz/*p}I=,F(p}.]{)YA*y#s.b<icC1-W97G0y}i_c#}Oxj)rG(<Ubo]
%]sEui-a4cX;+fyTspsTnYH[)l,x#(D(=3w6.ma.>r+VX-L6p55##+TyjN<}z/={
YR6J][n#cW7}Fjj)WZ#:YMsQxrek[1CA>+RqLZ;MV}JhZeDwq.F%m5<rq/l{5d*{
1)tiuiMs/-3n-}VKUAqe+6zrW.GuE0mO8+OY/>pw%b}WMh,R[[I7W]69}KN#<ElR
;(,ClbV1n>;An%)IT#MwZ/Q>w9gW]m=g1i#3d])}q*7bYmXDR1I*)L=#U33{537#
g[</wV5uAp23Z6[IRQC.r0wIa-g(tf=8Vm[qh#ORsB=/a4zsNzUJ%Gi*ade7vJ.=
E}O{o{;-#xxCYyq(.Yl#;d)IdV>IisMWR]fkaAujZG%t6[[f96rXl{R/]QRy.jXi
V)3NO:iTip7J{BXQlz#;n[Q-+31Z9{m>xD:+/jhZxxxX=d]Vmxg5#]tZb7k}vJGa
Y}sfONw7gu<16}c7>TbYZR%EAZL>yw6QGA)2A]{Ia3,OhgOvxoqQA>3tRl<xq3O=
:PB;/>2](O6>#s-Q{)#B[j][f}AnppmNUMkW8:zu1[_WRX)[RTy.1Q0=pMRs(8MF
J<;Bp1Dge8,*}w9)cHaM>Un.<<0NW{WvN.[]K)3.=9i/89z{IYqfw26ME]cb]>ou
[{R})#>CK{]###])###[#[)[[#(R])RR{{))(]]#]})RR]#=#]{}T==[])[)P_}]

(}[)[<R}##{(({uvE*=[}[#{#)}[)=)}}(}((({(###)R5,Q]#)##{#{##{#{{R{
RB_%m[8*TD3/qyZq3*<1GQDC:Y5F:YUT]8}9GaX9Mj7/8{]c)v7:GX,}y]kU#uwv
pu=#qdN[5gj]}RO3F[{2#C8T)vN5hNw0KC=;iY({)##]#RqL8<]A#h;Ol=poOq-z
R24JZE%w{jFw/Qx.a:mG7ZczR<IqB]z9A;i(c[nMN;.E)kjs}#Q5nLbDJCFH(u]I
pillH9f<,)IMo9C0=mMRAs#O:#{#OQwUCwf2#UR(GRAc,g/RBA<9#[)1ufV]ec}+
U<mD:9)YZ}ar6:GU61Lt-WRm87=Q(iFn2qQ[df;,8=dI<8(:iu))i]5Z[LIo2D(J
f([*G<U7[4[(AQ[}B9rK];ZCOm2x%QylYgOIJUJ%tc;p{v}5f3Da]jJF*Qt,y8)%
n}7Y7Nn{XJ0i*:X}zTmTtG,1HrNhbXjC961T[)E#IwJ#{{[*iB8T4Qym=YU#Or<,
;CG##%6+(yNUXC]j;jTzk=%HR%):bK-*Mn{nQ5Z:1sS*yh-O(D4=wF(f:GEb}TuY
X<Uuy0dk=]ezVXy+owfyk0pOu#=]6=<FN2TgM8H-p)=sKd#7H]=:+Znp.}[x)9iN
J]/G=)zswoNd[d(HZ5Lw8nXH/s#s<}tU(cC60e]eiiabxoFsf(x{a8x:(B27=b}U
w#)BVrv#<:GdCc,jdUmf:xBFRGNroY]8]Np]r#UrzXJ19O4yo)}-]RuZlx38*=RK
t=ADJ%hrgY(<#1Tine#H#ei.BbKF#ml{xfGLZMEJZcwNc181p7KWHbL,Q2}b8Hpm
4}QPUwm-HIc5.3y*RfJrZG2vEq(/AuQ8<%#/1QD0d;V#w7=}f))HTfbK%9#25(C+
p[Ep+%Fb:qK<FyAzHIFx=9YQ=[Vh2[H7vc1;4xZ+%FLqcl4l[IgJ-j4N5-pmH]%7
4)lMqQxBaCvG4T(j%FD/pJ9{ezYj-MK#falAlhEyr,c=mb}}F#w]n(jm#9nZ*k)R
2(Z{pnS)MD=(}UjX)eRA]RW211,7YcZ{-0*HNEMPHq5bKY}4(AzT{r)z.ZiRO]6#
-[A<7F.]ygMz+(s;KDh}ryOIT-ARWdYOb9fyz+i=KG;K=RnU;Q%7.r;)OnV3Di0#
2)2Qt7sD.0oMOp]<8V;Dw)QRMdvs}gzkMKVNxfeU}{LYDY]=L*<.+Tb5f1ForRa{
eej+2yl=Ma6W=Tn(O<EIZaCHQNRFUav=(1(}}=v{)%hC/Q(Zl]z=Jxy6={)Y9EY[
[)*#C-2B[Z#.5DvI#c8r/%Vb(fUC+.QvR23{a1B.ZT-;y63Ak:q4i8+tx9)d([0}
RT8XXd4:a1B6xg+8sA47Thq+;OQA2wlNzy:[%t#s<ka(y{dj[BICXT2JCudO=Ob)
):JGWhhmwaGyFa4H4KtLx4ckuy=6M#Dc<.U[)ke#XR[aLyn.#LU,R-[L[[R/G3y(
]K7]TMgWR=VRyE1}WhW{,9QUu)s*5bB8X:,Rc<zG5upMz;c,bnw:bbkrgEvq-pQ(
#m8RR}Y3%<XHGZsNdKf8Zd2<EEat#]M3Z7(c]/w1Kwpzsv=5MzhCWv]WkR=g;=oR
#x:)j]C=q-IaHprOai6guZZA5rmr3sAo,57M}r;t+=tcOA}[9lV#iu1,w-og8]I{
#2Q=)g:)HC[]zpgZgEx2fr7l*R<qB}:OD}60q(C)+KZ:]RfQ#lToFlR58iI7+Bj)
(/9vv-e;wxp,tj{vTd1F)YEcmMmR%=c<_r{;8rn(7Y[I#%I7r#hKRq]g:mRWbNx{
{c=j5xfn47I[}]9o<xTsWj7}iq:<uHB9W#VJ:ZMG:oM1oI9/zVKW6<[##I7(dtr#
R=gJ2<7s*(K<R-Z#mRI=m4J}h}RD:RdJ(e{)#[}j=k8glx[e01R#w2[XU1XafNE=
#DZ#)]]yRfvkhdX-Fiuz<8duCm,UC5WmZ-%aw.Ykb-kY9smbeCcaypR,[Z,MU<v}
]Rx*q9<}(]#}{#]#}(]{R.{](]R#}}{}[RvCbOlb0R[}{=u=)))#[#=)#({#[R)}
```

This dungeon contains tiles with peekers (marked `,` on the map) and pokers (marked `;`), along with getters and setters for register S (marked `s` or `S`).

Whenever you step onto a peeker tile, pop an argument `a` from the stack. Then read another number `b` from slot `a % S`, where S is the current stack size after popping the argument. Finally, push `b` onto the stack.

Whenever you step onto a poker tile, pop two arguments from the stack: first `b`, then `a`. Write `b` to slot `a % S`, where S is the current stack size after popping the arguments.

Whenever you step onto an S-getter tile, get the stack size as a number, then push that number onto the stack. For an S-setter tile, pop a number from the stack, then set the stack size to that number. This effectively only changes the stack pointer, while leaving the slots and their numbers unchanged, except for which slots are hidden.

After how many steps do you leave the dungeon?


## Example

Consider an example dungeon:

```
)]{(R{=(64sRr2=
)99s=3Rs#)S#r#S
#(Sr<}(s76}(R]4
]95)8#=5)R[##6=
[R=9s9{{{[###[)
```

Below is a log of walking through the example dungeon. The hidden slots above the stack are shown as `(n)`. Your location is marked `@` on the map.

```
Step count: 0
Coordinates: (1, 6, 0)
Direction: East
Next symbol: 3

Stack:
  ...
  (0)
  (0)
  (0) [S]


Non-zero registers:
  S: 26
  P: 97

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)@3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 1
Coordinates: (2, 6, 0)
Direction: East
Next symbol: (

Stack:
  ...
  (0)
  (0)
  (0) [S]

  3 [Top]

Non-zero registers:
  S: 27
  P: 98

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<@(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 2
Coordinates: (2, 6, 0)
Direction: Northeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  3 [Top]

Non-zero registers:
  S: 27
  R: -1
  P: 98

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<@(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 3
Coordinates: (2, 6, 0)
Direction: Northwest
Next symbol: 2

Stack:
  ...
  (0)
  (0)
  (0) [S]

  3 [Top]

Non-zero registers:
  S: 27
  R: -3
  P: 98

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<@(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 4
Coordinates: (1, 5, 0)
Direction: Northwest
Next symbol: =

Stack:
  ...
  (0)
  (0)
  (0) [S]

  2 [Top]
  3

Non-zero registers:
  S: 28
  R: -3
  P: 81

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#@#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 5
Coordinates: (0, 4, 0)
Direction: Northeast
Next symbol: r

Stack:
  ...
  (0)
  (2)
  (3) [S]


Non-zero registers:
  S: 26
  R: -1
  P: 64

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
@]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 6
Coordinates: (1, 3, 0)
Direction: Northeast
Next symbol: .

Stack:
  ...
  (0)
  (0)
  (2) [S]

  -1 [Top]

Non-zero registers:
  S: 27
  R: -1
  P: 49

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{@]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 7
Coordinates: (2, 2, 0)
Direction: Northeast
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (2) [S]

  -1 [Top]

Non-zero registers:
  S: 27
  R: -1
  P: 34

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2@s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 8
Coordinates: (2, 2, 0)
Direction: West
Next symbol: 2

Stack:
  ...
  (0)
  (0)
  (2) [S]

  -1 [Top]

Non-zero registers:
  S: 27
  R: -4
  P: 34

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2@s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 9
Coordinates: (1, 2, 0)
Direction: West
Next symbol: =

Stack:
  ...
  (0)
  (0)
  (0) [S]

  2 [Top]
  -1

Non-zero registers:
  S: 28
  R: -4
  P: 33

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=@.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 10
Coordinates: (0, 2, 0)
Direction: South
Next symbol: {

Stack:
  ...
  (0)
  (2)
  (-1) [S]


Non-zero registers:
  S: 26
  R: -6
  P: 32

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
@2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 11
Coordinates: (0, 2, 0)
Direction: Northeast
Next symbol: 5

Stack:
  ...
  (0)
  (2)
  (-1) [S]


Non-zero registers:
  S: 26
  R: -9
  P: 32

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
@2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 12
Coordinates: (1, 1, 0)
Direction: Northeast
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (2) [S]

  5 [Top]

Non-zero registers:
  S: 27
  R: -9
  P: 17

#[}}#=#R}{})#{]{
{@]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 13
Coordinates: (1, 1, 0)
Direction: South
Next symbol: 2

Stack:
  ...
  (0)
  (0)
  (2) [S]

  5 [Top]

Non-zero registers:
  S: 27
  R: -6
  P: 17

#[}}#=#R}{})#{]{
{@]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 14
Coordinates: (1, 2, 0)
Direction: South
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  2 [Top]
  5

Non-zero registers:
  S: 28
  R: -6
  P: 33

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=@.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 15
Coordinates: (1, 3, 0)
Direction: South
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -6 [Top]
  2
  5

Non-zero registers:
  S: 29
  R: -6
  P: 49

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{@]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 16
Coordinates: (1, 3, 0)
Direction: West
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -6 [Top]
  2
  5

Non-zero registers:
  S: 29
  R: -4
  P: 49

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{@]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 17
Coordinates: (1, 3, 0)
Direction: Southeast
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -6 [Top]
  2
  5

Non-zero registers:
  S: 29
  R: -7
  P: 49

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{@]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 18
Coordinates: (1, 3, 0)
Direction: North
Next symbol: 2

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -6 [Top]
  2
  5

Non-zero registers:
  S: 29
  R: -10
  P: 49

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{@]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 19
Coordinates: (1, 2, 0)
Direction: North
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (0) [S]

  2 [Top]
  -6
  2
  5

Non-zero registers:
  S: 30
  R: -10
  P: 33

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=@.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 20
Coordinates: (1, 1, 0)
Direction: North
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  2
  -6
  2
  ...

Non-zero registers:
  S: 31
  R: -10
  P: 17

#[}}#=#R}{})#{]{
{@]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 21
Coordinates: (1, 1, 0)
Direction: West
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  2
  -6
  2
  ...

Non-zero registers:
  S: 31
  R: -12
  P: 17

#[}}#=#R}{})#{]{
{@]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 22
Coordinates: (1, 1, 0)
Direction: Southeast
Next symbol: .

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  2
  -6
  2
  ...

Non-zero registers:
  S: 31
  R: -15
  P: 17

#[}}#=#R}{})#{]{
{@]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 23
Coordinates: (2, 2, 0)
Direction: Southeast
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  2
  -6
  2
  ...

Non-zero registers:
  S: 31
  R: -15
  P: 34

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2@s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 24
Coordinates: (3, 3, 0)
Direction: Southeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -15 [Top]
  5
  2
  -6
  ...

Non-zero registers:
  S: 32
  R: -15
  P: 51

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]@]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 25
Coordinates: (3, 3, 0)
Direction: Northeast
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -15 [Top]
  5
  2
  -6
  ...

Non-zero registers:
  S: 32
  R: -17
  P: 51

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]@]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 26
Coordinates: (3, 3, 0)
Direction: South
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -15 [Top]
  5
  2
  -6
  ...

Non-zero registers:
  S: 32
  R: -14
  P: 51

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]@]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 27
Coordinates: (3, 4, 0)
Direction: South
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -14 [Top]
  -15
  5
  2
  ...

Non-zero registers:
  S: 33
  R: -14
  P: 67

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{@[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 28
Coordinates: (3, 4, 0)
Direction: East
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -14 [Top]
  -15
  5
  2
  ...

Non-zero registers:
  S: 33
  R: -16
  P: 67

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{@[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 29
Coordinates: (3, 4, 0)
Direction: North
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -14 [Top]
  -15
  5
  2
  ...

Non-zero registers:
  S: 33
  R: -18
  P: 67

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{@[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 30
Coordinates: (3, 3, 0)
Direction: North
Next symbol: s

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -18 [Top]
  -14
  -15
  5
  ...

Non-zero registers:
  S: 34
  R: -18
  P: 51

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]@]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 31
Coordinates: (3, 2, 0)
Direction: North
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  34 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  S: 35
  R: -18
  P: 35

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.@}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 32
Coordinates: (3, 2, 0)
Direction: Southwest
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  34 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  S: 35
  R: -21
  P: 35

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.@}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 33
Coordinates: (3, 2, 0)
Direction: Northwest
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  34 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  S: 35
  R: -19
  P: 35

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.@}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 34
Coordinates: (3, 2, 0)
Direction: Northeast
Next symbol: 7

Stack:
  ...
  (0)
  (0)
  (0) [S]

  34 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  S: 35
  R: -17
  P: 35

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.@}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 35
Coordinates: (4, 1, 0)
Direction: Northeast
Next symbol: =

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  34
  -18
  -14
  ...

Non-zero registers:
  S: 36
  R: -17
  P: 20

#[}}#=#R}{})#{]{
{5]{@=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 36
Coordinates: (5, 0, 0)
Direction: Southeast
Next symbol: 8

Stack:
  ...
  (0)
  (7)
  (34) [S]

  -18 [Top]
  -14
  -15
  5
  ...

Non-zero registers:
  S: 34
  R: -15
  P: 5

#[}}#@#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 37
Coordinates: (6, 1, 0)
Direction: Southeast
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (7) [S]

  8 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  S: 35
  R: -15
  P: 22

#[}}#=#R}{})#{]{
{5]{7=@]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 38
Coordinates: (7, 2, 0)
Direction: Southeast
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  39 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  S: 36
  R: -15
  P: 39

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6@s;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 39
Coordinates: (7, 2, 0)
Direction: Southwest
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  39 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  S: 36
  R: -13
  P: 39

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6@s;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 40
Coordinates: (6, 3, 0)
Direction: Southwest
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (0) [S]

  -13 [Top]
  39
  8
  -18
  ...

Non-zero registers:
  S: 37
  R: -13
  P: 54

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6@}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 41
Coordinates: (5, 4, 0)
Direction: Southwest
Next symbol: ;

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  -13
  39
  8
  ...

Non-zero registers:
  S: 38
  R: -13
  P: 69

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[@4[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 42
Coordinates: (4, 5, 0)
Direction: Southwest
Next symbol: (

Stack:
  ...
  (0)
  (5)
  (-13) [S]

  39 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  X: 5
  S: 36
  R: -13
  P: 84

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[@78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 43
Coordinates: (4, 5, 0)
Direction: South
Next symbol: p

Stack:
  ...
  (0)
  (5)
  (-13) [S]

  39 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  X: 5
  S: 36
  R: -14
  P: 84

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[@78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 44
Coordinates: (4, 6, 0)
Direction: South
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (5) [S]

  100 [Top]
  39
  8
  -18
  ...

Non-zero registers:
  X: 5
  S: 37
  R: -14
  P: 100

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(@p{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 45
Coordinates: (4, 7, 0)
Direction: West
Next symbol: R

Stack:
  ...
  (0)
  (5)
  (100) [S]

  39 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  X: 5
  S: 36
  R: 100
  P: 116

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SR@(}#P(])][[#

---

Step count: 46
Coordinates: (3, 7, 0)
Direction: Northeast
Next symbol: p

Stack:
  ...
  (5)
  (100)
  (39) [S]

  8 [Top]
  -18
  -14
  -15
  ...

Non-zero registers:
  X: 5
  S: 35
  R: 39
  P: 115

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),S@R(}#P(])][[#

---

Step count: 47
Coordinates: (4, 6, 0)
Direction: Northeast
Next symbol: 7

Stack:
  ...
  (0)
  (5)
  (100) [S]

  100 [Top]
  8
  -18
  -14
  ...

Non-zero registers:
  X: 5
  S: 36
  R: 39
  P: 100

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(@p{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 48
Coordinates: (5, 5, 0)
Direction: Northeast
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (5) [S]

  7 [Top]
  100
  8
  -18
  ...

Non-zero registers:
  X: 5
  S: 37
  R: 39
  P: 85

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;@8#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 49
Coordinates: (6, 4, 0)
Direction: Northeast
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  7
  100
  8
  ...

Non-zero registers:
  X: 5
  S: 38
  R: 39
  P: 70

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[5@[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 50
Coordinates: (6, 4, 0)
Direction: South
Next symbol: 8

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  7
  100
  8
  ...

Non-zero registers:
  X: 5
  S: 38
  R: 42
  P: 70

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[5@[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 51
Coordinates: (6, 5, 0)
Direction: South
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  8 [Top]
  4
  7
  100
  ...

Non-zero registers:
  X: 5
  S: 39
  R: 42
  P: 86

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;7@#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 52
Coordinates: (6, 5, 0)
Direction: Northeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  8 [Top]
  4
  7
  100
  ...

Non-zero registers:
  X: 5
  S: 39
  R: 39
  P: 86

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;7@#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 53
Coordinates: (6, 5, 0)
Direction: Northwest
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (0) [S]

  8 [Top]
  4
  7
  100
  ...

Non-zero registers:
  X: 5
  S: 39
  R: 37
  P: 86

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;7@#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 54
Coordinates: (5, 4, 0)
Direction: Northwest
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  8
  4
  7
  ...

Non-zero registers:
  X: 5
  S: 40
  R: 37
  P: 69

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[@4[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 55
Coordinates: (5, 4, 0)
Direction: Northeast
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  8
  4
  7
  ...

Non-zero registers:
  X: 5
  S: 40
  R: 39
  P: 69

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[@4[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 56
Coordinates: (6, 3, 0)
Direction: Northeast
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (0) [S]

  39 [Top]
  5
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 39
  P: 54

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6@}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 57
Coordinates: (7, 2, 0)
Direction: Northeast
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (0) [S]

  39 [Top]
  39
  5
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 39
  P: 39

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6@s;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 58
Coordinates: (8, 1, 0)
Direction: Northeast
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  39
  39
  5
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 39
  P: 24

#[}}#=#R}{})#{]{
{5]{7=8]@)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 59
Coordinates: (8, 1, 0)
Direction: West
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  39
  39
  5
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 36
  P: 24

#[}}#=#R}{})#{]{
{5]{7=8]@)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 60
Coordinates: (8, 1, 0)
Direction: North
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  39
  39
  5
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 38
  P: 24

#[}}#=#R}{})#{]{
{5]{7=8]@)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 61
Coordinates: (8, 1, 0)
Direction: Southeast
Next symbol: ;

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  39
  39
  5
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 41
  P: 24

#[}}#=#R}{})#{]{
{5]{7=8]@)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 62
Coordinates: (9, 2, 0)
Direction: Southeast
Next symbol: [

Stack:
  ...
  (0)
  (4)
  (39) [S]

  39 [Top]
  4
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 41
  P: 41

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps@R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 63
Coordinates: (9, 2, 0)
Direction: Northeast
Next symbol: p

Stack:
  ...
  (0)
  (4)
  (39) [S]

  39 [Top]
  4
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 39
  P: 41

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps@R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 64
Coordinates: (10, 1, 0)
Direction: Northeast
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (4) [S]

  26 [Top]
  39
  4
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 39
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 65
Coordinates: (10, 1, 0)
Direction: East
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (4) [S]

  26 [Top]
  39
  4
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 40
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 66
Coordinates: (11, 1, 0)
Direction: East
Next symbol: ;

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  26
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 40
  P: 27

#[}}#=#R}{})#{]{
{5]{7=8]4)p@;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 67
Coordinates: (12, 1, 0)
Direction: East
Next symbol: (

Stack:
  ...
  (0)
  (5)
  (26) [S]

  39 [Top]
  4
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 40
  P: 28

#[}}#=#R}{})#{]{
{5]{7=8]4)p5@(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 68
Coordinates: (12, 1, 0)
Direction: Northeast
Next symbol: {

Stack:
  ...
  (0)
  (5)
  (26) [S]

  39 [Top]
  4
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 39
  P: 28

#[}}#=#R}{})#{]{
{5]{7=8]4)p5@(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 69
Coordinates: (12, 1, 0)
Direction: West
Next symbol: 5

Stack:
  ...
  (0)
  (5)
  (26) [S]

  39 [Top]
  4
  8
  4
  ...

Non-zero registers:
  X: 5
  S: 41
  R: 36
  P: 28

#[}}#=#R}{})#{]{
{5]{7=8]4)p5@(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 70
Coordinates: (11, 1, 0)
Direction: West
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (5) [S]

  5 [Top]
  39
  4
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 36
  P: 27

#[}}#=#R}{})#{]{
{5]{7=8]4)p@;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 71
Coordinates: (10, 1, 0)
Direction: West
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  26 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 36
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 72
Coordinates: (10, 1, 0)
Direction: Northwest
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  26 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 37
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 73
Coordinates: (10, 1, 0)
Direction: South
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  26 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 34
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 74
Coordinates: (10, 2, 0)
Direction: South
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (26) [S]

  5 [Top]
  39
  4
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 26
  P: 42

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;@69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 75
Coordinates: (10, 2, 0)
Direction: East
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (26) [S]

  5 [Top]
  39
  4
  8
  ...

Non-zero registers:
  X: 5
  S: 42
  R: 24
  P: 42

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;@69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 76
Coordinates: (11, 2, 0)
Direction: East
Next symbol: 9

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 24
  P: 43

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R@9R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 77
Coordinates: (12, 2, 0)
Direction: East
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 24
  P: 44

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R6@R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 78
Coordinates: (13, 2, 0)
Direction: Southeast
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (9) [S]

  6 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 9
  P: 45

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69@9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 79
Coordinates: (14, 3, 0)
Direction: Southeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 9
  P: 62

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}64@{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 80
Coordinates: (14, 3, 0)
Direction: Northeast
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 7
  P: 62

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}64@{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 81
Coordinates: (14, 3, 0)
Direction: East
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 8
  P: 62

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}64@{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 82
Coordinates: (14, 3, 0)
Direction: Northwest
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 5
  P: 62

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}64@{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 83
Coordinates: (13, 2, 0)
Direction: West
Next symbol: 9

Stack:
  ...
  (0)
  (0)
  (4) [S]

  6 [Top]
  5
  39
  4
  ...

Non-zero registers:
  X: 5
  S: 43
  R: 4
  P: 45

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69@9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 84
Coordinates: (12, 2, 0)
Direction: West
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 4
  P: 44

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R6@R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 85
Coordinates: (11, 2, 0)
Direction: West
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  9
  6
  5
  ...

Non-zero registers:
  X: 5
  S: 45
  R: 4
  P: 43

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R@9R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 86
Coordinates: (10, 2, 0)
Direction: North
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (6) [S]

  9 [Top]
  6
  5
  39
  ...

Non-zero registers:
  X: 5
  S: 44
  R: 6
  P: 42

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;@69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 87
Coordinates: (10, 1, 0)
Direction: North
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  26 [Top]
  9
  6
  5
  ...

Non-zero registers:
  X: 5
  S: 45
  R: 6
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 88
Coordinates: (10, 1, 0)
Direction: Southeast
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (0) [S]

  26 [Top]
  9
  6
  5
  ...

Non-zero registers:
  X: 5
  S: 45
  R: 9
  P: 26

#[}}#=#R}{})#{]{
{5]{7=8]4)@5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 89
Coordinates: (11, 2, 0)
Direction: Southeast
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  26
  9
  6
  ...

Non-zero registers:
  X: 5
  S: 46
  R: 9
  P: 43

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R@9R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 90
Coordinates: (12, 3, 0)
Direction: Southeast
Next symbol: ,

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 9
  P: 60

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}@44{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 91
Coordinates: (13, 4, 0)
Direction: Southeast
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 9
  P: 77

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.@p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 92
Coordinates: (14, 5, 0)
Direction: East
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  26
  9
  6
  ...

Non-zero registers:
  X: 5
  S: 46
  P: 94

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:@]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 93
Coordinates: (14, 5, 0)
Direction: South
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  26
  9
  6
  ...

Non-zero registers:
  X: 5
  S: 46
  R: 2
  P: 94

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:@]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 94
Coordinates: (14, 5, 0)
Direction: Southwest
Next symbol: s

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  26
  9
  6
  ...

Non-zero registers:
  X: 5
  S: 46
  R: 3
  P: 94

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:@]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 95
Coordinates: (13, 6, 0)
Direction: Southwest
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 3
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 96
Coordinates: (13, 6, 0)
Direction: Northwest
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 5
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 97
Coordinates: (13, 6, 0)
Direction: South
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 2
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 98
Coordinates: (13, 6, 0)
Direction: East
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 99
Coordinates: (13, 6, 0)
Direction: Southeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 1
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 100
Coordinates: (13, 6, 0)
Direction: Northeast
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  46 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: -1
  P: 109

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4@)#
),SRR(}#P(])][[#

---

Step count: 101
Coordinates: (14, 5, 0)
Direction: North
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (46) [S]

  6 [Top]
  26
  9
  6
  ...

Non-zero registers:
  X: 5
  S: 46
  R: 46
  P: 94

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:@]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 102
Coordinates: (14, 4, 0)
Direction: North
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (0) [S]

  78 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 46
  P: 78

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,@[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 103
Coordinates: (14, 3, 0)
Direction: North
Next symbol: 9

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  78
  6
  26
  ...

Non-zero registers:
  X: 5
  S: 48
  R: 46
  P: 62

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}64@{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 104
Coordinates: (14, 2, 0)
Direction: North
Next symbol: .

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 46
  P: 46

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R@)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 105
Coordinates: (14, 1, 0)
Direction: North
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 46
  P: 30

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(@=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 106
Coordinates: (14, 1, 0)
Direction: East
Next symbol: =

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 48
  P: 30

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(@=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 107
Coordinates: (15, 1, 0)
Direction: North
Next symbol: {

Stack:
  ...
  (0)
  (9)
  (4) [S]

  78 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 46
  P: 31

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.@
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 108
Coordinates: (15, 1, 0)
Direction: Southwest
Next symbol: 9

Stack:
  ...
  (0)
  (9)
  (4) [S]

  78 [Top]
  6
  26
  9
  ...

Non-zero registers:
  X: 5
  S: 47
  R: 43
  P: 31

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.@
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 109
Coordinates: (14, 2, 0)
Direction: Southwest
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (9) [S]

  9 [Top]
  78
  6
  26
  ...

Non-zero registers:
  X: 5
  S: 48
  R: 43
  P: 46

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R@)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 110
Coordinates: (13, 3, 0)
Direction: Southwest
Next symbol: .

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  9
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 43
  P: 61

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}6@4{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 111
Coordinates: (12, 4, 0)
Direction: Southwest
Next symbol: :

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  9
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 43
  P: 76

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp@,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 112
Coordinates: (11, 5, 0)
Direction: Southwest
Next symbol: 7

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 43
  P: 91

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#@{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 113
Coordinates: (10, 6, 0)
Direction: Southwest
Next symbol: (

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 43
  P: 106

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;5@}4s)#
),SRR(}#P(])][[#

---

Step count: 114
Coordinates: (10, 6, 0)
Direction: South
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 42
  P: 106

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;5@}4s)#
),SRR(}#P(])][[#

---

Step count: 115
Coordinates: (10, 6, 0)
Direction: West
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 44
  P: 106

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;5@}4s)#
),SRR(}#P(])][[#

---

Step count: 116
Coordinates: (9, 6, 0)
Direction: West
Next symbol: ;

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  7
  9
  4
  ...

Non-zero registers:
  X: 5
  S: 51
  R: 44
  P: 105

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;@7}4s)#
),SRR(}#P(])][[#

---

Step count: 117
Coordinates: (8, 6, 0)
Direction: West
Next symbol: r

Stack:
  ...
  (0)
  (5)
  (7) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 44
  P: 104
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r@57}4s)#
),SRR(}#P(])][[#

---

Step count: 118
Coordinates: (7, 6, 0)
Direction: West
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (5) [S]

  44 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 44
  P: 103
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{@;57}4s)#
),SRR(}#P(])][[#

---

Step count: 119
Coordinates: (7, 6, 0)
Direction: Southeast
Next symbol: P

Stack:
  ...
  (0)
  (0)
  (5) [S]

  44 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 41
  P: 103
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{@;57}4s)#
),SRR(}#P(])][[#

---

Step count: 120
Coordinates: (12, 2, 0)
Direction: Southeast
Next symbol: 4

Stack:
  ...
  (0)
  (5)
  (44) [S]

  9 [Top]
  4
  78
  6
  ...

Non-zero registers:
  X: 5
  S: 49
  R: 41
  P: 44
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R6@R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 121
Coordinates: (13, 3, 0)
Direction: Southeast
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (5) [S]

  4 [Top]
  9
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 50
  R: 41
  P: 61
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}6@4{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 122
Coordinates: (14, 4, 0)
Direction: Southeast
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  78 [Top]
  4
  9
  4
  ...

Non-zero registers:
  X: 5
  S: 51
  R: 41
  P: 78
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,@[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 123
Coordinates: (14, 4, 0)
Direction: Southwest
Next symbol: :

Stack:
  ...
  (0)
  (0)
  (0) [S]

  78 [Top]
  4
  9
  4
  ...

Non-zero registers:
  X: 5
  S: 51
  R: 43
  P: 78
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,@[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 124
Coordinates: (13, 5, 0)
Direction: Southwest
Next symbol: 4

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  78
  9
  4
  ...

Non-zero registers:
  X: 5
  S: 51
  R: 43
  P: 93
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{@R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 125
Coordinates: (12, 6, 0)
Direction: Southwest
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  4
  78
  9
  ...

Non-zero registers:
  X: 5
  S: 52
  R: 43
  P: 108
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}@s)#
),SRR(}#P(])][[#

---

Step count: 126
Coordinates: (12, 6, 0)
Direction: West
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  4
  78
  9
  ...

Non-zero registers:
  X: 5
  S: 52
  R: 44
  P: 108
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}@s)#
),SRR(}#P(])][[#

---

Step count: 127
Coordinates: (12, 6, 0)
Direction: Northeast
Next symbol: :

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  4
  78
  9
  ...

Non-zero registers:
  X: 5
  S: 52
  R: 47
  P: 108
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}@s)#
),SRR(}#P(])][[#

---

Step count: 128
Coordinates: (13, 5, 0)
Direction: Northeast
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (0) [S]

  4 [Top]
  4
  78
  9
  ...

Non-zero registers:
  X: 5
  S: 52
  R: 47
  P: 93
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{@R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 129
Coordinates: (14, 4, 0)
Direction: Northeast
Next symbol: {

Stack:
  ...
  (0)
  (0)
  (0) [S]

  78 [Top]
  4
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 53
  R: 47
  P: 78
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,@[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 130
Coordinates: (14, 4, 0)
Direction: West
Next symbol: ,

Stack:
  ...
  (0)
  (0)
  (0) [S]

  78 [Top]
  4
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 53
  R: 44
  P: 78
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,@[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 131
Coordinates: (13, 4, 0)
Direction: West
Next symbol: .

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  4
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 53
  R: 44
  P: 77
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.@p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 132
Coordinates: (12, 4, 0)
Direction: West
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  4
  4
  78
  ...

Non-zero registers:
  X: 5
  S: 53
  R: 44
  P: 76
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp@,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 133
Coordinates: (11, 4, 0)
Direction: West
Next symbol: S

Stack:
  ...
  (0)
  (0)
  (0) [S]

  75 [Top]
  5
  4
  4
  ...

Non-zero registers:
  X: 5
  S: 54
  R: 44
  P: 75
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sS@.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 134
Coordinates: (10, 4, 0)
Direction: West
Next symbol: s

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 75
  R: 44
  P: 74
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,s@p.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 135
Coordinates: (9, 4, 0)
Direction: West
Next symbol: ,

Stack:
  ...
  (0)
  (0)
  (0) [S]

  75 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 44
  P: 73
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,@Sp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 136
Coordinates: (8, 4, 0)
Direction: West
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 44
  P: 72
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[@sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 137
Coordinates: (8, 4, 0)
Direction: South
Next symbol: (

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 42
  P: 72
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[@sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 138
Coordinates: (8, 4, 0)
Direction: Southeast
Next symbol: [

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 41
  P: 72
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[@sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 139
Coordinates: (8, 4, 0)
Direction: Northeast
Next symbol: 9

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 39
  P: 72
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[@sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 140
Coordinates: (9, 3, 0)
Direction: Northeast
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  9 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 77
  R: 39
  P: 57
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]@[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 141
Coordinates: (10, 2, 0)
Direction: Southeast
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (9) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 9
  P: 42
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;@69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 142
Coordinates: (10, 2, 0)
Direction: West
Next symbol: ;

Stack:
  ...
  (0)
  (0)
  (9) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 12
  P: 42
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;@69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 143
Coordinates: (9, 2, 0)
Direction: West
Next symbol: s

Stack:
  ...
  (9)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 74
  R: 12
  P: 41
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps@R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 144
Coordinates: (8, 2, 0)
Direction: West
Next symbol: p

Stack:
  ...
  (0)
  (9)
  (0) [S]

  74 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 75
  R: 12
  P: 40
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6p@;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 145
Coordinates: (7, 2, 0)
Direction: West
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (9) [S]

  39 [Top]
  74
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 76
  R: 12
  P: 39
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6@s;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 146
Coordinates: (6, 2, 0)
Direction: West
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  39
  74
  0
  ...

Non-zero registers:
  X: 5
  S: 77
  R: 12
  P: 38
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r@ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 147
Coordinates: (5, 2, 0)
Direction: West
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  12 [Top]
  6
  39
  74
  ...

Non-zero registers:
  X: 5
  S: 78
  R: 12
  P: 37
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}@6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 148
Coordinates: (5, 2, 0)
Direction: Northeast
Next symbol: 8

Stack:
  ...
  (0)
  (0)
  (0) [S]

  12 [Top]
  6
  39
  74
  ...

Non-zero registers:
  X: 5
  S: 78
  R: 15
  P: 37
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}@6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 149
Coordinates: (6, 1, 0)
Direction: Northeast
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  8 [Top]
  12
  6
  39
  ...

Non-zero registers:
  X: 5
  S: 79
  R: 15
  P: 22
  H: 5

#[}}#=#R}{})#{]{
{5]{7=@]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 150
Coordinates: (7, 0, 0)
Direction: East
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (8) [S]

  12 [Top]
  6
  39
  74
  ...

Non-zero registers:
  X: 5
  S: 78
  R: 8
  P: 7
  H: 5

#[}}#=#@}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 151
Coordinates: (7, 0, 0)
Direction: Southwest
Next symbol: 8

Stack:
  ...
  (0)
  (0)
  (8) [S]

  12 [Top]
  6
  39
  74
  ...

Non-zero registers:
  X: 5
  S: 78
  R: 11
  P: 7
  H: 5

#[}}#=#@}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 152
Coordinates: (6, 1, 0)
Direction: Southwest
Next symbol: r

Stack:
  ...
  (0)
  (0)
  (0) [S]

  8 [Top]
  12
  6
  39
  ...

Non-zero registers:
  X: 5
  S: 79
  R: 11
  P: 22
  H: 5

#[}}#=#R}{})#{]{
{5]{7=@]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 153
Coordinates: (5, 2, 0)
Direction: Southwest
Next symbol: ]

Stack:
  ...
  (0)
  (0)
  (0) [S]

  11 [Top]
  8
  12
  6
  ...

Non-zero registers:
  X: 5
  S: 80
  R: 11
  P: 37
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}@6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 154
Coordinates: (5, 2, 0)
Direction: Northwest
Next symbol: 7

Stack:
  ...
  (0)
  (0)
  (0) [S]

  11 [Top]
  8
  12
  6
  ...

Non-zero registers:
  X: 5
  S: 80
  R: 13
  P: 37
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}@6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 155
Coordinates: (4, 1, 0)
Direction: Northwest
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  11
  8
  12
  ...

Non-zero registers:
  X: 5
  S: 81
  R: 13
  P: 20
  H: 5

#[}}#=#R}{})#{]{
{5]{@=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 156
Coordinates: (4, 1, 0)
Direction: East
Next symbol: =

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  11
  8
  12
  ...

Non-zero registers:
  X: 5
  S: 81
  R: 16
  P: 20
  H: 5

#[}}#=#R}{})#{]{
{5]{@=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 157
Coordinates: (5, 1, 0)
Direction: South
Next symbol: r

Stack:
  ...
  (0)
  (7)
  (11) [S]

  8 [Top]
  12
  6
  39
  ...

Non-zero registers:
  X: 5
  S: 79
  R: 18
  P: 21
  H: 5

#[}}#=#R}{})#{]{
{5]{7@8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 158
Coordinates: (5, 2, 0)
Direction: South
Next symbol: 6

Stack:
  ...
  (0)
  (0)
  (7) [S]

  18 [Top]
  8
  12
  6
  ...

Non-zero registers:
  X: 5
  S: 80
  R: 18
  P: 37
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}@6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 159
Coordinates: (5, 3, 0)
Direction: South
Next symbol: 5

Stack:
  ...
  (0)
  (0)
  (0) [S]

  6 [Top]
  18
  8
  12
  ...

Non-zero registers:
  X: 5
  S: 81
  R: 18
  P: 53
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]@r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 160
Coordinates: (5, 4, 0)
Direction: South
Next symbol: 7

Stack:
  ...
  (0)
  (0)
  (0) [S]

  5 [Top]
  6
  18
  8
  ...

Non-zero registers:
  X: 5
  S: 82
  R: 18
  P: 69
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[@4[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 161
Coordinates: (5, 5, 0)
Direction: South
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (0) [S]

  7 [Top]
  5
  6
  18
  ...

Non-zero registers:
  X: 5
  S: 83
  R: 18
  P: 85
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;@8#([#:{:R]
)<3(pp{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 162
Coordinates: (5, 6, 0)
Direction: South
Next symbol: (

Stack:
  ...
  (0)
  (0)
  (0) [S]

  101 [Top]
  7
  5
  6
  ...

Non-zero registers:
  X: 5
  S: 84
  R: 18
  P: 101
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(p@{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 163
Coordinates: (5, 6, 0)
Direction: Southeast
Next symbol: }

Stack:
  ...
  (0)
  (0)
  (0) [S]

  101 [Top]
  7
  5
  6
  ...

Non-zero registers:
  X: 5
  S: 84
  R: 17
  P: 101
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(p@{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 164
Coordinates: (5, 6, 0)
Direction: West
Next symbol: p

Stack:
  ...
  (0)
  (0)
  (0) [S]

  101 [Top]
  7
  5
  6
  ...

Non-zero registers:
  X: 5
  S: 84
  R: 20
  P: 101
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(p@{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 165
Coordinates: (4, 6, 0)
Direction: West
Next symbol: (

Stack:
  ...
  (0)
  (0)
  (0) [S]

  100 [Top]
  101
  7
  5
  ...

Non-zero registers:
  X: 5
  S: 85
  R: 20
  P: 100
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(@p{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 166
Coordinates: (4, 6, 0)
Direction: Southwest
Next symbol: R

Stack:
  ...
  (0)
  (0)
  (0) [S]

  100 [Top]
  101
  7
  5
  ...

Non-zero registers:
  X: 5
  S: 85
  R: 19
  P: 100
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(@p{r;57}4s)#
),SRR(}#P(])][[#

---

Step count: 167
Coordinates: (3, 7, 0)
Direction: West
Next symbol: S

Stack:
  ...
  (0)
  (0)
  (100) [S]

  101 [Top]
  7
  5
  6
  ...

Non-zero registers:
  X: 5
  S: 84
  R: 100
  P: 115
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),S@R(}#P(])][[#

---

Step count: 168
Coordinates: (2, 7, 0)
Direction: West
Next symbol: ,

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 101
  R: 100
  P: 114
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
),@RR(}#P(])][[#

---

Step count: 169
Coordinates: (1, 7, 0)
Direction: West
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 101
  R: 100
  P: 113
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
)@SRR(}#P(])][[#

---

Step count: 170
Coordinates: (1, 7, 0)
Direction: Northwest
Next symbol: )

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 101
  R: 101
  P: 113
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
)@SRR(}#P(])][[#

---

Step count: 171
Coordinates: (1, 7, 0)
Direction: North
Next symbol: <

Stack:
  ...
  (0)
  (0)
  (0) [S]

  0 [Top]
  0
  0
  0
  ...

Non-zero registers:
  X: 5
  S: 101
  R: 102
  P: 113
  H: 5

#[}}#=#R}{})#{]{
{5]{7=8]4)p5;(.=
=2.s}r6ps;R69R9)
{r]r]6r}]9[}644{
=]{r[54[,sSp.,p[
#2#[;78#([#:{:R]
)<3(pp{r;57}4s)#
)@SRR(}#P(])][[#

---

Step count: 172
```

You leave the example dungeon after 172 steps.
