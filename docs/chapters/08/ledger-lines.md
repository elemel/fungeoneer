## Chapter 8: Ledger Lines

You have entered the eighth dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnome sits on the bottom stair, sipping from a flask of mushroom brew. As he looks up at you, then down at the purse of stacking on your belt, you recognize him as the cartographer from the first dungeon. He leans forward, as if about to speak. With a magic marker and a flick of the wrist, he scribbles a line of credit onto your purse, in the shape of register S. He pauses for a moment, then sits back, taking another sip.

Register S serves as both stack size and stack pointer. It always points to the slot just above the top of the stack. Initially, register S points to slot 0, indicating that the stack is empty. Pushing writes a number to slot S, then increments S. Popping decrements S, then reads a number from slot S.

The stack is invalid if the stack size is less than 0, which is called stack underflow, or greater than the stack limit, called stack overflow.

With plenty of challenges ahead, you consult the map:

{% raw %}
```
#Rmj]=(=)[REWpdK>{}#]##}(R(R][]{bRRB_KR)=1P][=}{{}[{{(](]}}{#}R]R]#R)[==#)]]#R##
#1jpI{p>qEy>{}}{=H#A]{)ef)L4]Bl[4SbI0:dnNvFWz[ob{0Va40:*lUdtzDbqflVJ8tHrt{M}C(Y#
#ENUn][cpp3vNz=oTb+6=4-1gBpN(1le(.2(X#v(b>fk0AfgBf5Ym1{v*mAq+Sxm=U#}AJ%}p78Z=d}]
{hB.4}HNh}y[2vRy70+Jm=U/nAhUvgXUW>pLqVkIo]O(bNj>[C[Sf7[;gd#dwk7xu{X5DKqosyFU=8q[
#s[1b7dw=w/vQVdP.4nI(w]Fe-BJ}8vr>#=(G(%mY8XMaL>yV(D/sCN4Rs+4493Vxc-ZtNxVT0iTR+cR
[VMR)AlQc(Jvi4}Q)M-(q%5#w#FOO#]:]J]pY3,#[R5(+c;I#kHtzf6EiyL=I/r#C.]#bCLytl.Knwg[
RTJjgmoOwAy6=TT%-6VM8yDBbV55.2Lt*{=pHBduIC{=eBS52z3UBe{V/R[=tEUj}AvoNaqky>IaXJ+=
[c>{lGD=XdE=V+{0mV+wK=0qO[+]/z=X9#F=h/E:[DK7w{#u(t}Q5sHmVDN1R:V*RrR;QvRGA/qLlcy(
]zB_z1FgKN*)Zku#sc4Z{Cfy8WW>Vfy4]uumu#OyJQG:Z%)O_L>[bHEBcufnf34}9wl[wUIo#sc:2zI{
][RuuxEn*Xs8J>erIDBh=l2#m}a#Rp=8Q#l#ROi]>M16F/[({664)%=mh17#d1Fi#egjZY}#=hGK2(e#
)8Zi=#I0YDF+0cL)l+JUU)Db}34ux:#Op>*b0#B#*k))H{]#=fGtnWKjr8b=+IDZb>MxWfJx9gb=bY0)
Pq]J{((fCKVbJN*dXi]C]k<lG}Fqv#qEiFKrx(Eh_0X4EDAcLhyIbL*0t*Vajo2GKfztQ-sFtvoxR}8{
{]i#7B#Wok[Qpn6f#HpPc)p09YdH(O#H#y0#D)T)k:CqHJziq>8Gnv}93**]BcHi%CxLfsl*pJot.JL)
{M##88]EmBeLGZJ(Aim;ZjS[[tMvXha47cc72Wh#e0O2nDYm=B6l)nW_t9=}1r:=Tmp{x0xVk+{=v#Q[
)]rW#}#CD7L(q*+lTr#]7xV{](y8#x7*r*wpRn){y>TZ}#[=y4:+avfB1ppskVy9%2aY=BfBy:}n{IT)
{Qs0jtHLtrajAqR(.T0]EB+OJ99G3BHppic1JRLftp1H+usQ,pTv4bygo]#j/1T9NAzk}lH(WWItb}6}
#JE8j#{{>e8(yY(*ZV#6g(jz{#N#Z5]cL]OI0oYZ,3gdJ4/H9Vmw3tQ,j*)hgG[g:lR:%)sJR3K==nN}
#39)U2MD)41(YmN)j>V3WgM2CS1522+p6pi*ff-ko;rA}lY={#-lzY>l];Cllmsgb}l1})(RRzva{vK(
]L2VrNlkD=j=x7oV[t9v}K[N*.=##)->Wzy8ToCWq+l>Vdh>(K;c,gh=ye#V(8K*Hekq+:FzQ)%.71W]
##{#(}#[)))){)#]{#=})#]((P####{)]#{[)[[})[P)##R=[#=#=(}}-R}#=#{{{[#[Rs8([}#[)}{#

}]##=[#R(#]{(([{<W1)>](R}}{[)R={#[##}R#}##}(=#{=)R{}()}]]]R][{{][[#[]RN}{}[=#=))
R6z:+Y{<=R{<ns(rU.==T#(v=b9YCwQew{wr/>=[>TvhpbAHx[YJvy2fQnp.yVG3-.5(M5MT8do(sJf_
(q-ZmgqolDk>iJzZUI>pB3qTx[bx7vx[JOfY{tJM3<D;[J9Dgpg7TIeYMQ1gIOwZVlVkrm)-y5]]#q9]
=2mOhpb]mi{eBv{#2#x}*{c}PFP48k>bI<A;qpY)Cex#Sdd<>b*tXf(U(V8[7f}Ka}=ag=>HK5O(rRW#
R-9OkIlbL/6R*}n2}l).JoNRVR[2E#0[<>(/wr)qk((/,k<xM.8Uc77y+{(D>J2WtjNWauKl5,:Gbl2]
zNwELMHrv=W=3>H,VR)l05)YD{SG4Zvd>n;0d=n77yZ(x}0/i#jorehJ2zm>8ylJ)[vph1(#kSK-n8yR
pJD(RZ5>]Kc5f-ab%1/.=h+{ctG[9#1zm*Xv(=:hI64>/iVGYA33.D[P-Ui8Q)8R[)kV9+a9r<D*juQ{
[;<SCT0wRDIe2)+34fKE8Uql79i(=:XTI5BeBF{zTUTBTsYeI3=QGhEkDuFXDRN]tSn6N{0+)fMV)CU}
#Hq.Dc[>2)l+c5g4[pyF[>gU#)M<*A#Lh5N)XQ2cGdRmXc}G*T<uk8d7R(wRs2ZY(2br57kr6X(p5Op(
[CR[v(3kT7Jgs<h+J(B.rW).u2w1/y:E;Uti)x=2<}D#*FxV9Y)9(8f}Lngg.}z:.8%R#gQGI#l#.A%}
[69W0u7>nX%ypZpGF>[sdudsu1sFY,8iT<a/Zxorv;0.0qif==sUZ:=k)h[+pE[z.<IkW#/y#6#Pv9I(
[zomM5>%4pWu:R{]jqap/6fs23gR)0fm>:.%]LGW#+r#Y>zr>8nh0Rp=/*c[BrvBa8)dM-a#Z#6#m=6R
}o7ey[1}0EO*]-2#yh0[]47KC.,16An0htuh-SexCp6i5MUO2<6Qb#]39p(wJ*tJ1Y-dKrc4#4#xQ.}=
)YR/21==NhWE-OF2TFD}8Oxza{u#-:#Au}RjLls9R.iz.lotZXL)p]r]3q*z4SogWM%5IrgoBIgph+1#
{n((DZUeOeeYT-54/g[j.NY.>.h0>pY7cKwg(z{:G<>I8g:hs=i7>LnJQ+)za>c{yykX.>#6f#)OXJb}
(VtG*NHAD%e9krhC-vJ4K/x]V-Iz%FcMa.roYt+[)Rz>}u%5Y8kL)#E#7%W#{(J,#Zxt1l[Y.XCzV:n{
[Is9phT><n(i#4[x(HS{J4{{]k=k,gSD+)Ep(>#%n(Zw.-nO(1vxsg8xS/qX#=-St}p7(rMVv}aqvbL{
{7>.k3aGDx]fKgknk<=FA4qkK)R)CKEBuR{]R{O#l})=(a(ZuZFcTZ<[[#{#[rRo0C(Co{=Iu]vCpCx#
)u(-9I2S995.U4ZCkcZ)I6/O=bl2Ug4<:e;_[:BTtQ%<>Q[<2L[+}xT(,XB-DjX/hApiE9bvZA5*EHh[
)({}{]]#{}hsR}qBR({[##][)}(R(]]R]R(}.R#P)#R{##P}]]]#[[)RB>#[}Rm{=#([]R(]]_###{##

#########]()(RhAOwWR<[[[}#_R=R){}=>[[=)}[){[#{[#]#][}}})}#}([]}}#[}{=2/j)[{{[({#
[S>######]IABLy0o9qJt()ycttXCtmiIThD*<ik<Nh>7-t=(G##-#URuz7Epjvk9Z7]-2Bd8=]Cf(J#
}JJi7%jAHiL<##yE>v<3o)Bnjf(}4(7.sg]vs1i.xdkt>9/iXDtsIszAWR{A9aDN[XdZXjVloXbH=L,#
{>mp;7nTdXJ:vQvhQO=n[fgq8L.dqG<uoJr*74zG{]c6X%E#<=4I>[p/RTXbq5d/e5a{:{<0}uR{}#2#
[e#z#####+[}{#=ou%>C%OK2>[8FLa(d,<yT=2TS#d#y)hVDbVCa2bFqN-Uo<h1vLmNR)%7xAfL4bkB=
)aiouF7oxjta(<pJ%83-)d_%lrSO[Vt*<ywFn1,[l]5)kdY9E47>N*+RGR)<#6w=I>n#8OY2(#0]yH>5
[yNtq:{<#boFIx4(R_AV:iH4R)X{#uf):N*]aZ%m0Y#<cE+6DflRVnWw2D[XFIh{8;B/9]vKZzFbv>VR
#*#(#{dY9=fDQw:y.ak%s{kZSgcqxcLx-Far-*oWsEk;wXZj]2oX2#nzG}Lh2z[Rbt.4twl]Ta#CN9))
(y-gvb(<kA39.g}>eTv)6<skk=:j=TW=Od=N),w:Hcp.HXstLuj=[:upW5*q]L>rm)eW76-W:uY9j-9]
{-##[pxf>:iDl*b>dAR-=lsi=gjJbeVe=Vy(u0t9(kn9rE7=;2iB[s[e]4v#-Nt[gk(bw#x#eZuabE(}
(>RW%2j<Kuweoz[Ge<iE)mqn5xx9/GfbNJyZuG(GSrFdQiq=#J#KT}DN-QRCEG#ac#N#j=fF>RC)D}>[
]G}u,.<[EZ24LA=*]#O3t-[joI{Rl12D<#k>Oq+)xt[]j<i#<ZLC74)yfSbbRjc{.CuF0Ftnlv}nd{vR
VzW,g-)pGWNy*fHz{8l8OKTc6cc)%p#VJ]coA,Lkn/F{p=0d)wc-)]+N82J6IwlReRUzJ=/()LMR2Jk[
sK#.#40[JduHx-iGQ;h>mzD.i{t0g7:l4nw]]Kep*R=>}+Z)0l6Tuhm8KJWvzLjOCLw7IcZ>tqoGR7AX
i*x#R.-3Lq[8VXRa.zzE9mrD<1i(<B->IfrR3hH/Fe<3>fM{%=R8<Sayfh)63<dH7##(R<4R*ip1vhI=
JI};u9yk:10u){{k#=7a}]PpH0]py75M>)F]JR3fZr*<V)vk={UZb6CK}6A(8]d>opv4+NcMMNh]V*9[
RV:neVK<3kieHzi=Xq[M=(}9w-t6ROr7*)j[(<lI/]im[T=1(=/6EBFwBp/dUKhMn1{}G7b[xs+qe4x(
#h<>8WMcSbA+LY*qtdn)Kdk2>](Et{7UI0Jo}gK}}XgSM9066AH}n7Uozl(HvI1-UWZq6KyjVhvxQS-{
}UtU3gm6}a26[8pYzb%=*cWJg1ZvpeL3F)Q3hNBbo:u]<rBR2mR=[)#Tz)]}))##di/86(([[{([{9][
#[#}=)R5D=}{{R=[)]yR_}]}R.%{]]}))}R[[[R[(]=[=[]#]IyeugG=}<XpWlUAo[)Rt0-asftSFxm(

][]])]){[}(({P#[{]{(TTTRP=#=[(]_{}<R#[}{#=(#)){#{#]RxzX9R=R[[))})=)}}##]#]#{#]({
(w<j2h27L48YBjEVbP6C}{dAVY4U*cVvCy-eRx*Jn[j<,-{##s{#>Oxv>H>9WrF0h1,2+6TJG:Q6[J2R
]VERuTao1=i[Qe%W<,;Ul}Vx%l=)JR:nls;YZY(VBQgY<[>##{R8yF}-]#q3V#ko/pb]u9>1y.jH}-Yl
p<#+Z/u[uf2}pR5#;q[)qf7+D))i(8MklkIBjv{z8h8qMxNWI*-R<#v#5R2ry5CYCJz*K6auIl9B-v>8
=VKd%YGHQt3b+>=ONx<4FgJ:<elV1gALLTRcVf#7lMJ#A(6+KeYxmQ4N2RxS06)AMW9#h9k=Q8Q)2[]i
#u#9:{d3cpWhG[Rm0#[=b#2C=x)t3Y=DgHw4kfRF[9vh#RkhoFn<eG4>D)/0V}:#K<q/U]J{cmHr1><G
]Nij#Kf,X%65[95{jKo*M+{2{/RDxLNaNZu8OglIT>n99y4DtqnGNvqIQufpQI))j[EDWegkN+Lm1<pH
{gk+rf6fmKBM(c>>5=RC0*f=w-svJ#Ucj;RCv17kJaFdEbw7BpX39nP/X()wv[Gvtqq(>)2}KH92tDWp
{mm)(f4%n8NFsuL<2v+Hb]]l(5(ygd#wNp>[>Y3UX(L>a6](>T2#y#i]>HZL:n<]5[y(-(o[pbUNp}N}
=(VL[+g}<]u0UE{<NRb{T(1hu{a75{[g+5NA4c=w+kzo]DllXIT;XDgXq}(VOG3s9t8drja/RWAptYN(
R<IFr*>m*.M/*YaF1kBRgeO{S}03#tglJ-SfV=gHY(7;#7-p=kg[3[lr0Idf{;QYp=}L%M0B<=5*(H<}
(WRo9g(Mo*y9-Ip/nv2Zue}1KC31{#D+(Gx<Rm>f#aUv#).*czrMZ,76-,3px*mCiIq=>WB8LM*vz(a}
]vdz=rZ>DVz(B2bNH}sAqx-iMn3w[g}fv>RZ%#Bk;#q;e/(#LV5);[m(8A]i>Qi}eW{eoX{(X(x)Ebu[
=IgdKXuq;ui(rqM#c)7<CZ0[X(h3n2myk(>Af9qc##*<:qd-(HUg6urmbN(BV,5#5#eGY]n<D-7k6B}#
}Yr0cb2px;p-jP[]+e-=xji37p;8:t=<-ltSi70U}#OC<62]q7{o{]qt][AnF9]0d/fIK:{,:0R#D#q#
]n)]#71h[NXG(a#W,>3Vsw51:Yg[ohW7<pa77iLh#oudWx(JK)MqO*(Z1*i8qVv<.#8V4)R5n[pK#Kr]
[E*:/cyclD-UIxrZs:frOL/}Uwf=s5Kdsie*5)e+R-7.=KF>9q3R=L]:/#G:DTy=6Mt9t4HY9]mE%#X#
[aG<3LJVO6:6EqjH3/)D/Yi#<Ib{y9q[hAnbt9bNNzjjasmD0Q2R]5y/[TF9Fym#/If=>}Y,)zG,8ig[
(l7k}B5BdD8:p/ZLI/Zm]F(:w00bh[XKGbIS(_cQ#6CrR(})=};Kh))=){onwLzc+[amT#{}}#[#}g##
}[[#}}[#{)}]({({}()=(]][){#{}#{}]}}RQ[}}##R>9JswtLR=RqTD/w=({}]]#(R]RL04:p::*+Y{

#}#)]]=){[(RM})}}#[RR{={}(]#{#{(_}{=(#](]#>hn3v,ielqpm2XLR]}_]]R#R]R[#}##[[]P#(}
}r]tTETSzvj-{aR(]ntnCzWL,2}#2}3m;tDrkTO4E0fi0TH1L5IN<##[<.<tRojal.u=Rln##}B>WnG=
(44f3*+25dylEYc)cYeV;DBaHXbN7n=(}z=h9)TT]#]#}#<(}}#}}A}*bv>UOT;H[(RX(R<E#peMIgp{
].lDL}s#.2#pZ{zupRb)gijQ{)M=NR-aamLYhp.vH);w.dD1s28(CrUJ.E+lbHi.elMQG]q#OL#6RB<R
{cK6iVuI>>:Lu<61Iz+o5D2pWM2ga%jm6M*ELnsHQ)A:K-y>a6HNkqij;fjYZwa63:{6W[}nK>R=QcrC
]D8)WF1VDK#c{9>m({R)H5fL6NiXG6LwtG+DgF-RzT]XLD##(sraDK8<sidZGMMip%{c{vT[Jq}Dz<2]
)%HGWhDpe0:MvoVM5yB>lUeA[Y#5+s[(0=%e6xs=w<XCK7FyB5YLiM)Q%ef=MfFyzwIjw4DoF>]]sq>#
#H]3Io=z}eaF>A<<Ru}E}#Cbm>s4e5)f#v#E5wLnQn7I[kEuX8SaKylkXsK9[N3e(]-2<Q#5[L==CR>{
#kPW90YF2#{G5.A8lop#:h45]yD#teoO+]<h<w(f3%%<%S4(<T1#F)Kg<)qO]gs[c27FxK{>B[#7JMc=
#V})(5d{m:RrKv3c0=1Zo6i-W2#chO#2b(AUEss%ZCc7d3=w#+IRz3W-ReV},=yl/a59cAWb4iLeL[g{
(GZki7<jSIDQYyafw]e)nr+o#kkO.=p4)}[v5e)T7A3b1DC5iusjM#ycTHHHGm#]KZ+k:xV>R#v]lk3E
[UmIJ=TxJj-w}J]>ROA1O)sEXzhv5p5XB]a(2M<WQjT#lV#7S/q7HW](31JZ(qaMb4cx<fmq(uw)4xKE
(711]s]<ZY1c+{AD:yXRxw5;(9ncI[df0<R2vitucQAUCXvA+d2%kHur0Jpm<=+N{6(M10/A[CtVq69=
}IW=l;%yXhG:mTD,2Du1SI>H+W#{+u]LYd<IN2B5=#pvq>*k#n{->5))xOzd5.r#7Zo8/OzgVGZkAHs}
]Cwk[v6/KK4=Q*C0wpWbM)DU==>#>GdslsSkLYh5c:cps[J>5{F,F#JrL6c868OC>R#qv[X]0ve=c:L{
#XcV>{]]v4y)]->UY<u)i+oW+Glo)dkRR8+d*[-DN%UdyZ(1#lWu>wuqj;cJGbgOK>22.#YN]e{xL5o#
#9B2N8.}U55I6;x}7b(jGenaG###6#]%pweyXeJbRBc-lj9<)2[g[oI{=>r*y1O)*t#RmiQzcQVMFr,[
{:r=W/)XraM(S:#RxrB}xRHyO-K9Jxkl5Hk5iKZE(ag2[p>DogJ:[}(}#}=#]#]=y2s6<*UD>l1zha)}
(qZ5JIVufS92:;b.}l*5*}X0-OY.6%w2B4j3yU>hgc*{-7w(UDL87ggX5f63kaLV]q9X6tp8Qn1tY4p}
[[R}#}}##[(({#[#[#[[R}}#]=[)#(R]D=[)(R[{)Cl<[){[[RpAt.jHWvCAm.L(}#{}{###[}==}]])

##}##]#RJrb+Z}{)](]#=]](R}{#]{(zk/yE+MQyv-<R(=})R=gXej=GYUBm1h=N4aY8b+I4j7Webum}
##h#FRa)W](j[g[+JrN]X%m9s(x[79C7HUceBVWH+5sjBHN>gngR}=5[[[R}=kJu=ta={Tg:ALH<Rk]#
##rJ*3a>3vu.]Fj7Wxw#J(D60-[0f[ao[}}({(>{#{]Bs4Si]q9RGa8E>(<V0opsksep.rG%)))#g{GP
]{KVZ#RZx90QtVx){ir}WtaYBcA,k]+u32sFBafyn=fSxdEtzUw/.gegdfisxYW7TiU7l.:>_e4kxT-[
)gvulSlQ<<k9R.6f=q8Sq#/VS4V#.YZXsVjNSBD[.}##kF#<lK:#j)b#-s5#9k#ieOhzB[##R<D#5ER{
[Jo9.pv[0R=AD[<t=k-9k[Ceb>aZt7Y=9:LSo{vsEIGgUa3O7IY%sz37gEfo>[QD-B/F4EAar:6rk;B)
)v{{Ifv9))Ow#-qRs>5<>p##W]oC8>w;Vxn*#U%V}:;q==nquJ2+8{YNw(Kc=Bvb{3}H2{R](<FL=L<{
}=Kk7+b*}bVN<ke*pyztXp4*B<6bV)7nOia(tUDD9ykrjb(8(2#[QywETUG,>+7#=}9ZcB{29.2LDJ<#
()}yC(.#N[#rE#hBx=Yal(-ZZtM#E-{5iX29jk/a79[j:tgjMRXCO6E65Wyx.a4HMJ0s%pw<dAZhQK]{
]5ubRJuX,:hEpM9XZ:bYHI5Rja903MyAxn-j{KbTwM[(x7x[-gD/yBm*DI9lVXqvpkF=Rj(={p{-vkv}
>=b[q2Q[o#ja#==-3EdCVnd}J3T*=c1qNAFX3VX(6V1M88Z154US[k:GccS=-TAu]IsE)ll<18D>yny[
(Nc3j:Gehm.Nh+.<puO}OEyRopyFuh8H[YYe/{(Kfs=/i]joloJVk#iW%RCwgwMB>oC#:)Xd[nx=}Dg#
{]-(TVW(e5bE[(>7jw5Q-NvM0k1*5emB+ZTfOi>Jtao;67T+A7m4uz6wvcxAKC{(Wq9e]%Th}Npy##3=
{j+xGYbN>}gg2r[k5y=WST<JI;Usff1RlbkuM8705>}J8<{v]Sn#<JnZXGTA}p;]6+YZfr*mvU2FAYp]
{)s>>jEFRf7-z[3b(NXYUsgiDV<L<qGrYq5URls6bmUZJx:<:a%)r#YL]CmxQbv3<3FZUE7Kx{#AKeD[
#L#=<dFehW#eGf<8+>e=O4n#Q:##:c3>{4Ogdz1Gp:MDWAn7z=a%<#%RUGX0Lhizl<+B(m=6dX0h7YY]
RUc;MO2>zQNUCK)+#F:a%[}h9co#E=#+;W[>agm1J6I#r*d6(c{/HweJR<E[>hN#y#8V2>KY[stW5ni#
[eVET8NCSiB2IzhAM:F5dt2.z]}d2#RhN,OsrDZEB}#c,w<7rI}#dtGy(#KAg)4[=g%zM7oi<>/RoaU}
]Hy18MJEHsf.:OeUKD4};N:]}RR>G{)>CNLQe3<=Z44}HBTXFGvb1BzK%hhuRwOl:Cr33tz>}D{>8}rR
}[#[[#{R#(}{=(]{R({#{{{}6MIh=7Dr=)=###{{](]]){R{R{#=([R{##(}}R]))}#]#}}]#[})))[}

[GbF4AW-tIOe:sR)]{#)]##]{([))}#=RD/NbK}{RR{=[[([[R#R>c*}[=))))}{##{#)][Pbz=}}{##
#r6u3eqnlT0e7b]4I}S6/}CMmZ9CM6HIniG7m-e/-n2m.Dl<,*g%hsqYw]ze+M1Z2ZGI)%0-7G>aOy[]
{j8uwSk<]#[{8f#5kvLZJ[#0}ij}f0#}#k4qR}<)sEEG(N#v)h#q0Xc4<f}r-{#0)ZeRk[(}QUm6V8B#
RwD-}##>{4yNGh;>}k.Zord;r,u#ZfZ#}}sz(2(=cy%mL(GqE(X[O(k)8{F#bniwNM.O)wQ<q){g)dt=
(bitV%BXi>8)y>h)Xq22AN5vgbDl68C5(BTj0Bmlke4FXA=s,h)Mk*g3NRjtalq(}nD2t8R8EE2m,,K[
RFc>t>}#;FU[s+,#24qYX)[[E<S#QC)>NggWSKF:-/%SBz6x6}iF9jU7HE1n<1ZUSkU[li##}ji/b6i)
]g=6RKj5FU4U(4[cO<zg<=#JO/x9y<blEhh3l>X]O{NJy9C.0>58{bXQ{rZw]J#.AH(K=8]>v>)s%(2#
[Vm2Z#1(0V1]>rX{O31HyndWK#4d7enX)JE{-DDNu.rA#X).WwXZ(Jm#=hN><;#Ow}/}l).f>cD3W:3{
#zX}m9#X5wh}t(LUryRN-RJ/b[{+bXa#[/#OLLedCt1Mu#[gJVLOB+{C)k#D]jUK}Y=[>.kjc6rz)),#
[2%1sFj{VY/rt(tz9dwx]T*1k7UaqJvweE3c2=LZV8hA>yDi6i(z-=4=Z(gk)0RAq>s(BJX(BDDRMpV}
<shv0%xrFKr#*YDwd6lw37fGQ7,7xxQndd2K)9CeZK>u(JBh%[K::5G.g8jj1TxD[niskl)qga(<}k>{
D/wUI4WscO:pw)DhYX[hzS[ZC3eK%r)3bM0nJM++js}q5g}e#qA(Mjy2W0)bF8d.<zk4==qMD[>/a=B}
Q[WN=Ep+FI3JC2<Im2LG4v4x4cx}5r)}oWd.sq<wl:4%TwFk4KVlA*vN%F1(7NJj}iKmy9[E7WXr#gH(
>#avs],u<d8zqy)#8qEBREUEnu#}6o*]#.[2C=Vgy<aq6pyOfvvzT[SfcTdc2StYiiwI3gEi-k8>yEi)
#}n<<rIa}C28TZ}jRENpGNFfgRFToMEGa3NLZ]fnxYtI3{9r.E>Ow4K7=27TFQI=dZgcmkqb*r-nA41}
#0d{{6}{a1;{>bj;z<A9.sJAKB=((s><RKB+Z(aO(2>JYvnu:((N}Vc%Vpt*HY72Z5NT[c}B(,sO[8G#
(nZ;m[0<rXeYsviQYf,R0>]QzMf}}}e#m*v<U}[XfnIEYiH{A5+ew>U(4j).<TKb5]6#(<i#SK-M=tS]
{]DkC0H(]c1#=;+At.}zE7Q}[}Xc=A7J(dVX.ssB>leDw7T7sT>0=.)Nq={TcDKrSqVURH#2[<9=jF1{
##g}32Sept12-Q{yvCyWLj3wcCw<=Hx<}R]c=))K=mRo[}(])#][]#vWq{zwgBMN)8j*cLA<duZ<Pd+)
#}{{(])#)}}9==P}][)[})7Op*xEf/1ZG0aoL-y,tR#RBdpt0UDbX%({#=[{{{[}[[)}{]#]=}=#=}R[

))R+azgC+R#]{}{([(]}]#}{#={]Reh%BEFlW5rur){R(R){}#)R<]{])){={(=#[##[=){=Dt3)##{#
}b+N({={RtWRajALnehl9Usbjgu{[b#}((:+cp/K1Cu3=x]v#zY,_Rl2Atv]6t1m{T7rwq%;te<s:-E[
o40DlJpYzdflcNy*xqA}w#dRHI=W[}yBaJ{=V]RJ)0T{8kf18TjW%2xlgx1ohq0eT.vX(*]G#bR{yn[#
idL=CqN<wze[r5v<g0R=j2bEVR+[jR1b_}84a{i3Y%#5}0+1#txmp]xy=;,o}sjnQ0V5lSYmsFNYdnu#
=2RW=NV]K<89W<GvVB=6RsoQkP3fY+rwiQK:)T}RkAw#rRzecV-t5{.[#QWKz-99c92ayfSsAL]-{#J#
]Rs<7<C1,YwN.u0(N7,:6oCFv:qUg6F<b+F8dR[S%m-5Dk:hqmubBHkwcTRek]eyB=Ek]5,+(srF0BQ]
=XLh#StCj=Bnf2u+A*%M.0ege()#fY*pn{,+}<Zk4Y9En)ZTs<s==RWTh#}(Q#m1xRKZfVr<;<ME8yZ)
(sm}[E1qJx1p<Q+s]=Lc8I=xrF##/s65YAy1)]jckVm7pfrY+D,0jQnA4.0<r*#AM[04UhTB<4zNFrf]
]p=O;rW+ahKl[]#L/6Rq-)+#]AIsjRry7co.MOcwaM9/I40h64oZ5z*lztDRlLy{[CmF<w{%=(e02J9]
=})itu{or6n(-{[aTd6BED/###e7e{dd4dS7[c)=-_##<d=TuHnjpe6Ky4tDOr{Gx<xOTT.3YDbfK[7{
}3z{*6fr.=L0}Q#7gZo9pFG[#v#sV{)I53HwT#C(,R<#}:t9w)r*Nz1U(+J[-[[}25D5pv;X(eLI.K<(
)AG;JBQR0)6+r3D=h4k)YKKLO#)#3NTamWZ{}.qdd..eK0E-x25K8UNxtH*yJrCDh}xq1ziLrR<A:Fd{
(H)ygjkM*nrc-t+X%Dg95W51]KY7a4378DMFA}CQRgt*b[GHl,Ty3[n60XRM9)cz.jJn}}}(Jnm:WAv#
<T}qjaxbv8GtIfdn1Kl%b9s=Xyi.aGlpG*6*Vp)Qa7g0cEH:EZZ7TQc4JUfgDsV{}G]e}qw6Vnx<;#S[
wh]c}Bqh4y#k#:TXsMH*=y+n]19dp##LwQWZ]#qK#{70]mfiLU<q1(Y=hH##*ncR=Sz%=KVm#IuL(E:[
3E)R#6J)r}e#<]{Rrv{)I6.{FUr(M#<K=f=;(W#t#Z<,Rm/l9Jt6/w({UwItkwY=6jpzNag.5BH3602#
zk[TX8Dwxk)oNBa-YFK6=<=yx[pU=Q6l9FFVhl}SRU)2H8]j/RRxY<:*-bAbU[Ac#=7Xvn0hMz;Qu[k[
:*)iP;Yrj1}V)#Rp=Dtn,;Q+3aZl*Ohn84Kl[)v9<d}+[AiAG(<{OrNCrD%=s]8+.a=gcGf/#(%i]KQR
=-RXRMm]WgW[0W70sk1N0sKs=)]{6ekLFCuDoUch]M)oX5tErxzO8XL2TO(w;H(.{CYJmA9Ws{#6X*L(
#]](]{]]})]#Rv4p*[]I2Nn4MfcL=(R={}R)]]p={#=)#]]]]###}][]=)][({}{#((R}{]i-Di=R])#
```
{% endraw %}

This dungeon contains tiles with peekers (marked `,` on the map) and pokers (marked `;`), along with getters and setters for register S (marked `s` or `S`).

Peekers and pokers access a unified view of stack and inventory. They apply to the stack for an address of zero or higher, or the inventory for a negative address. Registers A through Z are mapped to address -1 through -26, respectively.

Whenever you step onto a peeker tile, pop an argument `a` from the stack. Then get another number `b` from slot `a`. Finally, push `b` onto the stack.

Whenever you step onto a poker tile, pop two arguments from the stack: first `b`, then `a`. Set the number in slot `a` to `b`.

Whenever you step onto an S-getter tile, get the stack size as a number, then push that number onto the stack. For an S-setter tile, pop a number from the stack, then set the stack size to that number.

After how many steps do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/08/ledger-lines.md).


### Example

Consider an example dungeon:

{% raw %}
```
{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))
```
{% endraw %}

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show the stack size (labeled `S`).

{% raw %}
```
{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09@[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: []  Dx: East  Co: (4, 2, 0)  TC: 0
P: 44  R: 0  S: 0

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09@[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: []  Dx: North  Co: (4, 2, 0)  TC: 1
P: 44  R: -2  S: 0

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09@[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: []  Dx: Southeast  Co: (4, 2, 0)  TC: 2
P: 44  R: 1  S: 0

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r@16[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: Southeast  Co: (5, 3, 0)  TC: 3
P: 65  R: 1  S: 1

---

You turn right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r@16[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: Southwest  Co: (5, 3, 0)  TC: 4
P: 65  R: 3  S: 1

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r@16[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: North  Co: (5, 3, 0)  TC: 5
P: 65  R: 6  S: 1

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r@16[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: West  Co: (5, 3, 0)  TC: 6
P: 65  R: 4  S: 1

---

You get 4 from R.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9@916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 9]  Dx: West  Co: (4, 3, 0)  TC: 7
P: 64  R: 4  S: 2

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R@r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 4, 9]  Dx: West  Co: (3, 3, 0)  TC: 8
P: 63  R: 4  S: 3

---

You set R to 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)@9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 9]  Dx: Southeast  Co: (2, 3, 0)  TC: 9
P: 62  R: 9  S: 2

---

You set R to 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80@}{]#[{(R=={{)#))

St: [9]  Dx: West  Co: (3, 4, 0)  TC: 10
P: 83  R: 4  S: 1

---

You push 0.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}8@R}{]#[{(R=={{)#))

St: [0, 9]  Dx: West  Co: (2, 4, 0)  TC: 11
P: 82  R: 4  S: 2

---

You push 8.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}@0R}{]#[{(R=={{)#))

St: [8, 0, 9]  Dx: West  Co: (1, 4, 0)  TC: 12
P: 81  R: 4  S: 3

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}@0R}{]#[{(R=={{)#))

St: [8, 0, 9]  Dx: Northeast  Co: (1, 4, 0)  TC: 13
P: 81  R: 7  S: 3

---

You set R to 8.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)@9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 9]  Dx: East  Co: (2, 3, 0)  TC: 14
P: 62  R: 8  S: 2

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R@r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 0, 9]  Dx: East  Co: (3, 3, 0)  TC: 15
P: 63  R: 8  S: 3

---

You get 8 from R.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9@916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 9, 0, 9]  Dx: East  Co: (4, 3, 0)  TC: 16
P: 64  R: 8  S: 4

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r@16[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 8, 9, 0, 9]  Dx: East  Co: (5, 3, 0)  TC: 17
P: 65  R: 8  S: 5

---

You push 1.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r9@6[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 9, 8, 9, 0, 9]  Dx: East  Co: (6, 3, 0)  TC: 18
P: 66  R: 8  S: 6

---

You push 6.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r91@[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (7, 3, 0)  TC: 19
P: 67  R: 8  S: 7

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r91@[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 1, 9, 8, 9, 0, 9]  Dx: North  Co: (7, 3, 0)  TC: 20
P: 67  R: 6  S: 7

---

You push 0.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{@}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 6, 1, 9, 8, 9, 0, 9]  Dx: North  Co: (7, 2, 0)  TC: 21
P: 47  R: 6  S: 8

---

You peek 9 from slot 0.

{=][(#[([=[}[734R(}#
]r76}##@s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 6, 1, 9, 8, 9, 0, 9]  Dx: North  Co: (7, 1, 0)  TC: 22
P: 27  R: 6  S: 8

---

You turn forward-left.

{=][(#[([=[}[734R(}#
]r76}##@s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 6, 1, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (7, 1, 0)  TC: 23
P: 27  R: 5  S: 8

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##@s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 6, 1, 9, 8, 9, 0, 9]  Dx: Southwest  Co: (7, 1, 0)  TC: 24
P: 27  R: 3  S: 8

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##@s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (7, 1, 0)  TC: 25
P: 27  R: 0  S: 8

---

You get 8 from S.

{=][(#[([=[}[734R(}#
]r76}##,@:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (8, 1, 0)  TC: 26
P: 28  R: 0  S: 9

---

You swap 9 and 8.

{=][(#[([=[}[734R(}#
]r76}##,s@96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (9, 1, 0)  TC: 27
P: 29  R: 0  S: 9

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:@6[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (10, 1, 0)  TC: 28
P: 30  R: 0  S: 10

---

You push 6.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: East  Co: (11, 1, 0)  TC: 29
P: 31  R: 0  S: 11

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: North  Co: (11, 1, 0)  TC: 30
P: 31  R: -2  S: 11

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Southeast  Co: (11, 1, 0)  TC: 31
P: 31  R: 1  S: 11

---

You push 3.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[@27=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [3, 6, 9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Southeast  Co: (12, 2, 0)  TC: 32
P: 52  R: 1  S: 12

---

You set R to 3.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587@#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 9, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Southwest  Co: (13, 3, 0)  TC: 33
P: 73  R: 3  S: 11

---

You turn right because 9 > 6.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R@={{)#))

St: [9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (12, 4, 0)  TC: 34
P: 92  R: 5  S: 9

---

You push 8.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[15@7R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (11, 3, 0)  TC: 35
P: 71  R: 5  S: 10

---

You push 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}5@[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 8, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (10, 2, 0)  TC: 36
P: 50  R: 5  S: 11

---

You swap 8 and 4.

{=][(#[([=[}[734R(}#
]r76}##,s@96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 4, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (9, 1, 0)  TC: 37
P: 29  R: 5  S: 11

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s@96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 4, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: Southwest  Co: (9, 1, 0)  TC: 38
P: 29  R: 3  S: 11

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s@96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 4, 9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: North  Co: (9, 1, 0)  TC: 39
P: 29  R: 6  S: 11

---

You turn left because 4 < 8.

{=][(#[([@[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: West  Co: (9, 0, 0)  TC: 40
P: 9  R: 4  S: 9

---

You turn left.

{=][(#[([@[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 8, 6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (9, 0, 0)  TC: 41
P: 9  R: 2  S: 9

---

You swap 8 and 9.

{=][(#[([=[}[734R(}#
]r76}##,s@96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (9, 1, 0)  TC: 42
P: 29  R: 2  S: 9

---

You push 5.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}@4[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [5, 8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (9, 2, 0)  TC: 43
P: 49  R: 2  S: 10

---

You push 1.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[@587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 5, 8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (9, 3, 0)  TC: 44
P: 69  R: 2  S: 11

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[@587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 5, 8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: Northeast  Co: (9, 3, 0)  TC: 45
P: 69  R: -1  S: 11

---

You push 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}5@[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 1, 5, 8, 9, 6, 1, 9, 8, 9, 0, 9]  Dx: Northeast  Co: (10, 2, 0)  TC: 46
P: 50  R: -1  S: 12

---

You push 6.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 4, 1, 5, 8, 9, 6, 1, 9, 8, ...]  Dx: Northeast  Co: (11, 1, 0)  TC: 47
P: 31  R: -1  S: 13

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 4, 1, 5, 8, 9, 6, 1, 9, 8, ...]  Dx: Northwest  Co: (11, 1, 0)  TC: 48
P: 31  R: -3  S: 13

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:9@[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 4, 1, 5, 8, 9, 6, 1, 9, 8, ...]  Dx: Southwest  Co: (11, 1, 0)  TC: 49
P: 31  R: -5  S: 13

---

You push 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}5@[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 6, 4, 1, 5, 8, 9, 6, 1, 9, ...]  Dx: Southwest  Co: (10, 2, 0)  TC: 50
P: 50  R: -5  S: 14

---

You push 1.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[@587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 4, 6, 4, 1, 5, 8, 9, 6, 1, ...]  Dx: Southwest  Co: (9, 3, 0)  TC: 51
P: 69  R: -5  S: 15

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[@587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 4, 6, 4, 1, 5, 8, 9, 6, 1, ...]  Dx: Southeast  Co: (9, 3, 0)  TC: 52
P: 69  R: -7  S: 15

---

You turn forward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[@587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 4, 6, 4, 1, 5, 8, 9, 6, 1, 9, 8, ...]  Dx: East  Co: (9, 3, 0)  TC: 53
P: 69  R: -8  S: 15

---

You push 5.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1@87R#,)#]R
}80R}{]#[{(R=={{)#))

St: [5, 1, 4, 6, 4, 1, 5, 8, 9, 6, 1, 9, ...]  Dx: East  Co: (10, 3, 0)  TC: 54
P: 70  R: -8  S: 16

---

You push 8.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[15@7R#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 5, 1, 4, 6, 4, 1, 5, 8, 9, 6, 1, ...]  Dx: East  Co: (11, 3, 0)  TC: 55
P: 71  R: -8  S: 17

---

You push 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[158@R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 8, 5, 1, 4, 6, 4, 1, 5, 8, 9, 6, ...]  Dx: East  Co: (12, 3, 0)  TC: 56
P: 72  R: -8  S: 18

---

You set R to 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587@#,)#]R
}80R}{]#[{(R=={{)#))

St: [8, 5, 1, 4, 6, 4, 1, 5, 8, 9, ...]  Dx: Northeast  Co: (13, 3, 0)  TC: 57
P: 73  R: 7  S: 17

---

You push 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[32@=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 8, 5, 1, 4, 6, 4, 1, 5, 8, ...]  Dx: Northeast  Co: (14, 2, 0)  TC: 58
P: 54  R: 7  S: 18

---

You get 18 from S.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=@;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [18, 7, 8, 5, 1, 4, 6, 4, 1, 5, ...]  Dx: Northeast  Co: (15, 1, 0)  TC: 59
P: 35  R: 7  S: 19

---

You set R to 18.

{=][(#[([=[}[734@(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 8, 5, 1, 4, 6, 4, 1, 5, 8, 9, ...]  Dx: South  Co: (16, 0, 0)  TC: 60
P: 16  R: 18  S: 18

---

You poke 7 into slot 8.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s@4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [5, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, ...]  Dx: South  Co: (16, 1, 0)  TC: 61
P: 36  R: 18  S: 16

---

You go south.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=@}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [5, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, ...]  Dx: South  Co: (16, 2, 0)  TC: 62
P: 56  R: 18  S: 16

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=@}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [5, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: Southwest  Co: (16, 2, 0)  TC: 63
P: 56  R: 19  S: 16

---

You peek 1 from slot 5.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#@)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: Southwest  Co: (15, 3, 0)  TC: 64
P: 75  R: 19  S: 16

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#@)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, 9, ...]  Dx: East  Co: (15, 3, 0)  TC: 65
P: 75  R: 16  S: 16

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#@)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: Southeast  Co: (15, 3, 0)  TC: 66
P: 75  R: 17  S: 16

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#@)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, ...]  Dx: South  Co: (15, 3, 0)  TC: 67
P: 75  R: 18  S: 16

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#@)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: Northeast  Co: (15, 3, 0)  TC: 68
P: 75  R: 15  S: 16

---

You go northeast.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=@}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: Northeast  Co: (16, 2, 0)  TC: 69
P: 56  R: 15  S: 16

---

You push 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;@#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 1, 1, 4, 6, 4, 1, 5, 7, 9, ...]  Dx: Northeast  Co: (17, 1, 0)  TC: 70
P: 37  R: 15  S: 17

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;@#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: South  Co: (17, 1, 0)  TC: 71
P: 37  R: 18  S: 17

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;@#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 1, 1, 4, 6, 4, 1, 5, 7, 9, ...]  Dx: Northwest  Co: (17, 1, 0)  TC: 72
P: 37  R: 21  S: 17

---

You set R to 4.

{=][(#[([=[}[734@(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [1, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, 9, ...]  Dx: West  Co: (16, 0, 0)  TC: 73
P: 16  R: 4  S: 16

---

You push 4.

{=][(#[([=[}[73@R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4, 1, 1, 4, 6, 4, 1, 5, 7, 9, 6, 1, ...]  Dx: West  Co: (15, 0, 0)  TC: 74
P: 15  R: 4  S: 17

---

You push 3.

{=][(#[([=[}[7@4R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [3, 4, 1, 1, 4, 6, 4, 1, 5, 7, 9, 6, ...]  Dx: West  Co: (14, 0, 0)  TC: 75
P: 14  R: 4  S: 18

---

You push 7.

{=][(#[([=[}[@34R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 3, 4, 1, 1, 4, 6, 4, 1, 5, 7, 9, ...]  Dx: West  Co: (13, 0, 0)  TC: 76
P: 13  R: 4  S: 19

---

You turn left.

{=][(#[([=[}[@34R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 3, 4, 1, 1, 4, 6, 4, 1, 5, 7, ...]  Dx: South  Co: (13, 0, 0)  TC: 77
P: 13  R: 2  S: 19

---

You set S to 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[@=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (13, 1, 0)  TC: 78
P: 33  R: 2  S: 7

---

You push 2.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[3@7=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [2, 6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (13, 2, 0)  TC: 79
P: 53  R: 2  S: 8

---

You set R to 2.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587@#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 1, 9, 8, 9, 0, 9]  Dx: South  Co: (13, 3, 0)  TC: 80
P: 73  R: 2  S: 7

---

You turn left because 1 < 6.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=@{{)#))

St: [9, 8, 9, 0, 9]  Dx: East  Co: (13, 4, 0)  TC: 81
P: 93  R: 0  S: 5

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=@{{)#))

St: [9, 8, 9, 0, 9]  Dx: Northwest  Co: (13, 4, 0)  TC: 82
P: 93  R: -3  S: 5

---

You push 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[158@R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 9, 8, 9, 0, 9]  Dx: Northwest  Co: (12, 3, 0)  TC: 83
P: 72  R: -3  S: 6

---

You turn left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[158@R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 9, 8, 9, 0, 9]  Dx: Southwest  Co: (12, 3, 0)  TC: 84
P: 72  R: -5  S: 6

---

You set R to 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(@=={{)#))

St: [9, 8, 9, 0, 9]  Dx: Northeast  Co: (11, 4, 0)  TC: 85
P: 91  R: 7  S: 5

---

You push 7.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[158@R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 9, 8, 9, 0, 9]  Dx: Northeast  Co: (12, 3, 0)  TC: 86
P: 72  R: 7  S: 6

---

You push 2.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[3@7=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [2, 7, 9, 8, 9, 0, 9]  Dx: Northeast  Co: (13, 2, 0)  TC: 87
P: 53  R: 7  S: 7

---

You turn right because 7 > 2.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S@s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 8, 9, 0, 9]  Dx: Southeast  Co: (14, 1, 0)  TC: 88
P: 34  R: 9  S: 5

---

You turn left because 8 < 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327@.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 0, 9]  Dx: Northeast  Co: (15, 2, 0)  TC: 89
P: 55  R: 7  S: 3

---

You poke 9 into slot 0.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s@4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: Northeast  Co: (16, 1, 0)  TC: 90
P: 36  R: 7  S: 1

---

You turn forward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s@4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9]  Dx: North  Co: (16, 1, 0)  TC: 91
P: 36  R: 6  S: 1

---

You set R to 9.

{=][(#[([=[}[734@(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: []  Dx: Southeast  Co: (16, 0, 0)  TC: 92
P: 16  R: 9  S: 0

---

You push 4.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;@#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4]  Dx: Southeast  Co: (17, 1, 0)  TC: 93
P: 37  R: 9  S: 1

---

You get 37 from P.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}@r
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [58, 4]  Dx: Southeast  Co: (18, 2, 0)  TC: 94
P: 58  R: 9  S: 2

---

You set R to 58.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]@
}80R}{]#[{(R=={{)#))

St: [4]  Dx: South  Co: (19, 3, 0)  TC: 95
P: 79  R: 58  S: 1

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]@
}80R}{]#[{(R=={{)#))

St: [4]  Dx: Southwest  Co: (19, 3, 0)  TC: 96
P: 79  R: 59  S: 1

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]@
}80R}{]#[{(R=={{)#))

St: [4]  Dx: West  Co: (19, 3, 0)  TC: 97
P: 79  R: 60  S: 1

---

You turn right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]@
}80R}{]#[{(R=={{)#))

St: [4]  Dx: North  Co: (19, 3, 0)  TC: 98
P: 79  R: 62  S: 1

---

You get 62 from R.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}p@
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [62, 4]  Dx: North  Co: (19, 2, 0)  TC: 99
P: 59  R: 62  S: 2

---

You set P to 62.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)@9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [4]  Dx: North  Co: (2, 3, 0)  TC: 100
P: 62  R: 62  S: 1

---

You push 0.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}@9<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 4]  Dx: North  Co: (2, 2, 0)  TC: 101
P: 42  R: 62  S: 2

---

You push 7.

{=][(#[([=[}[734R(}#
]r@6}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 0, 4]  Dx: North  Co: (2, 1, 0)  TC: 102
P: 22  R: 62  S: 3

---

You turn right.

{=][(#[([=[}[734R(}#
]r@6}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 0, 4]  Dx: East  Co: (2, 1, 0)  TC: 103
P: 22  R: 64  S: 3

---

You push 6.

{=][(#[([=[}[734R(}#
]r7@}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 7, 0, 4]  Dx: East  Co: (3, 1, 0)  TC: 104
P: 23  R: 64  S: 4

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r7@}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 7, 0, 4]  Dx: Southwest  Co: (3, 1, 0)  TC: 105
P: 23  R: 67  S: 4

---

You push 0.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}@9<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 6, 7, 0, 4]  Dx: Southwest  Co: (2, 2, 0)  TC: 106
P: 42  R: 67  S: 5

---

You turn forward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}@9<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 6, 7, 0, 4]  Dx: West  Co: (2, 2, 0)  TC: 107
P: 42  R: 68  S: 5

---

You turn backward-right.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}@9<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [0, 6, 7, 0, 4]  Dx: Northeast  Co: (2, 2, 0)  TC: 108
P: 42  R: 71  S: 5

---

You push 6.

{=][(#[([=[}[734R(}#
]r7@}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 0, 6, 7, 0, 4]  Dx: Northeast  Co: (3, 1, 0)  TC: 109
P: 23  R: 71  S: 6

---

You turn forward-left.

{=][(#[([=[}[734R(}#
]r7@}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 0, 6, 7, 0, 4]  Dx: North  Co: (3, 1, 0)  TC: 110
P: 23  R: 70  S: 6

---

You turn left.

{=][(#[([=[}[734R(}#
]r7@}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 0, 6, 7, 0, 4]  Dx: West  Co: (3, 1, 0)  TC: 111
P: 23  R: 68  S: 6

---

You push 7.

{=][(#[([=[}[734R(}#
]r@6}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 6, 0, 6, 7, 0, 4]  Dx: West  Co: (2, 1, 0)  TC: 112
P: 22  R: 68  S: 7

---

You get 68 from R.

{=][(#[([=[}[734R(}#
]@76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [68, 7, 6, 0, 6, 7, 0, 4]  Dx: West  Co: (1, 1, 0)  TC: 113
P: 21  R: 68  S: 8

---

You turn right.

{=][(#[([=[}[734R(}#
]@76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [68, 7, 6, 0, 6, 7, 0, 4]  Dx: North  Co: (1, 1, 0)  TC: 114
P: 21  R: 70  S: 8

---

You turn left because 7 < 68.

{@][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 0, 6, 7, 0, 4]  Dx: West  Co: (1, 0, 0)  TC: 115
P: 1  R: 68  S: 6

---

You turn backward-left.

{@][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [6, 0, 6, 7, 0, 4]  Dx: Southeast  Co: (1, 0, 0)  TC: 116
P: 1  R: 65  S: 6

---

You push 7.

{=][(#[([=[}[734R(}#
]r@6}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [7, 6, 0, 6, 7, 0, 4]  Dx: Southeast  Co: (2, 1, 0)  TC: 117
P: 22  R: 65  S: 7

---

You push 9.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}0@<[{0}54[327=.}pr
#)R9r916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [9, 7, 6, 0, 6, 7, 0, 4]  Dx: Southeast  Co: (3, 2, 0)  TC: 118
P: 43  R: 65  S: 8

---

You get 65 from R.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9@916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [65, 9, 7, 6, 0, 6, 7, 0, 4]  Dx: Southeast  Co: (4, 3, 0)  TC: 119
P: 64  R: 65  S: 9

---

You turn backward-left.

{=][(#[([=[}[734R(}#
]r76}##,s:96[S=s;4#P
#}09<[{0}54[327=.}pr
#)R9@916[1587R#,)#]R
}80R}{]#[{(R=={{)#))

St: [65, 9, 7, 6, 0, 6, 7, 0, 4]  Dx: North  Co: (4, 3, 0)  TC: 120
P: 64  R: 62  S: 9

---

You go upstairs.

St: [65, 9, 7, 6, 0, 6, 7, 0, 4]  Dx: North  Co: (4, 2, -1)  TC: 121
P: -56  R: 62  S: 9
```
{% endraw %}

You leave the example dungeon after 121 steps.
