clear,clc
%initial
disp('initial')
object=convertCharsToStrings(input('object?','s'));%輸入想要讀取的object
tic
cd(object)%換到image目錄
voxelbox=ones(100,100,100);
Inst=[722.481995 0.000000 399.000000;0.000000 722.481934 311.000000;0.000000 0.000000 1.000000];
Ext01=[0.508468 0.860935 -0.015857 3.932282;-0.101237 0.041482 -0.994003 21.303495;-0.855111 0.507022 0.108232 88.085114];
Ext02=[0.054555 0.997525 0.044349 -0.396882;-0.129876 0.051127 -0.990217 21.030863;-0.990031 0.048262 0.132325 86.551529];
Ext03=[-0.483178 0.864219 0.140232 -6.133193;-0.118992 0.093863 -0.988454 21.073915;-0.867401 -0.494281 0.057464 88.905014];
Ext04=[-0.826707 0.562054 0.025509 -3.706015;-0.015798 0.022133 -0.999636 22.618803;-0.562411 -0.826804 -0.009437 89.343170];
Ext05=[-0.920328 -0.386141 0.062375 0.837949;-0.102550 0.084312 -0.991155 20.728113;0.377463 -0.918577 -0.117211 93.253716];
Ext06=[-0.315707 -0.948836 -0.006217 2.520231;-0.091609 0.037001 -0.995114 20.983803;0.944422 -0.313592 -0.098622 93.845718];
Ext07=[0.547250 -0.836131 -0.037448 -5.300584;-0.082565 -0.009407 -0.996548 21.209290;0.832886 0.548449 -0.074202 91.918419];
Ext08=[0.998758 -0.047722 -0.014321 7.249783;-0.026645 -0.268707 -0.962861 16.707335;0.042101 0.962035 -0.269661 101.258018];
Ext09=[0.515633 0.856808 0.001705 1.082603;0.856751 -0.515573 -0.013213 4.623665;-0.010425 0.008264 -0.999911 114.083206];
Ext10=[-0.164361 0.974144 -0.155012 2.258266;-0.915024 -0.209267 -0.344892 8.572358;-0.368429 0.085148 0.925748 76.273094];
Ext11=[-0.053241 0.998369 0.020604 1.405633;-0.737301 -0.053217 0.673473 -20.414452;0.673454 0.020664 0.738940 80.795265];
Ext=cat(3,Ext01,Ext02,Ext03,Ext04,Ext05,Ext06,Ext07,Ext08,Ext09,Ext10,Ext11);%合併成一個變數方便計算
clear Ext01 Ext02 Ext03 Ext04 Ext05 Ext06 Ext07 Ext08 Ext09 Ext10 Ext11

%讀image
img01=rgb2gray(imread('01.bmp'));
img02=rgb2gray(imread('02.bmp'));
img03=rgb2gray(imread('03.bmp'));
img04=rgb2gray(imread('04.bmp'));
img05=rgb2gray(imread('05.bmp'));
img06=rgb2gray(imread('06.bmp'));
img07=rgb2gray(imread('07.bmp'));
img08=rgb2gray(imread('08.bmp'));
img09=rgb2gray(imread('09.bmp'));
img10=rgb2gray(imread('10.bmp'));
img11=rgb2gray(imread('11.bmp'));
img=cat(3,img01,img02,img03,img04,img05,img06,img07,img08,img09,img10,img11);%合併成一個變數方便計算
clear img01 img02 img03 img04 img05 img06 img07 img08 img09 img10 img11
%%
%calculate
disp('calculate')
for i=1:11%11個image
    for z=1:100
        for y=-49:50
            for x=-49:50
                if voxelbox(x+50,y+50,z)==1%判斷是否已經被清除
                    check_img_pixel=Inst*Ext(:,:,i)*([x y z 1])';%Camera Model
                    check_img_pixel=round(check_img_pixel/check_img_pixel(3));%將座標改為正確的座標(非外星人座標)
                    if check_img_pixel(1)>0 && check_img_pixel(1)<=798 && check_img_pixel(2)>0 && check_img_pixel(2)<=622%檢查是否在image中
                        if img(check_img_pixel(2),check_img_pixel(1),i)==0%檢查image像素值是否為0
                            voxelbox(x+50,y+50,z)=0;%將空間voxel清除
                        end
                    else
                        voxelbox(x+50,y+50,z)=0;%不在image中的直接將空間voxel清除
                    end
                end
            end
        end
    end
    disp(i);%顯示跑到第幾張圖
end
%%
%save voxel coordinate
voxelco=[];
for z=1:100
    for y=-49:50
        for x=-49:50
            if voxelbox(x+50,y+50,z)==1
                voxelco=[voxelco;x y z];%將物體座標存入變數以便輸出
            end
        end
    end
end
name=append(object,'.xyz');
dlmwrite(name,voxelco,'\t')%輸出xyz檔
cd ..
disp('done')
toc
