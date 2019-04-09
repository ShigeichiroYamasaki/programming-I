■■　　授業資料URL
https://drive.google.com/drive/folders/0Bwts5UTHjM9EUS14V0w0OEMyUzQ?hl=ja

第13回：ハッシュ

■課題の回答案

data=[["女", 30], ["女", 45], ["女", 68], ["女", 47], ["女", 56], ["男", 48], ["男", 31], ["女", 45], ["女", 32], ["男", 35], ["男", 54], ["男", 46], ["女", 54], ["女", 72], ["女", 41], ["男", 40], ["男", 77], ["女", 36], ["男", 55], ["男", 52]]


def taiju(data)
  sum_of_men=0
  sum_of_women=0
  num_of_men=0
  num_of_women=0
  data.each do |d|
    if d[0]=="男" then
      sum_of_men=sum_of_men+d[1]
      num_of_men=num_of_men+1
    else
      sum_of_women=sum_of_women+d[1]
      num_of_women=num_of_women+1
    end
  end
  return [sum_of_men.to_f/num_of_men, sum_of_men.to_f/num_of_men]
end

処理例
p taiju(data)
=> [48.666666666666664, 47.81818181818182]

また、以下のプログラムによって生成されるデータでも実行してください
data=(1..100).map{|x|[['男','女'][rand(2)],rand(50)+35]}


■ハッシュの例

h={"年齢"=>60,:性別=>"男", 0=>[1,2,3]}
p h


■ハッシュの値取り出しの例

h={"年齢"=>60,:性別=>"男", 0=>[1,2,3]}
p h["年齢"]
p h[:性別]
p h[0]

■ハッシュの作成方法

h={}
# キーと値の登録
h["年齢"]=60
h[:名前]="山崎"
# ハッシュオブジェクトの確認
p h

■未定義のキーの返り値

h={}
h["年齢"]=60
h[:名前]="山崎"
# 未定義のキーでアクセス
p h[:abcd]

■シンボルによるハッシュの作成方法

h={}
h[:名前]="山崎"
h[:年齢]=60
p h

■シンボルをキーにしたハッシュの簡略表現

h={名前: "山崎", 年齢: 60}
# Ruby言語の内部では => 表記になっている
p h

■ハッシュに対するメソッド

h={"名前"=>"山崎", "年齢"=>60}
p h.keys

■ハッシュに対するメソッド

h={"名前"=>"山崎", "年齢"=>60}
p h.values

■ハッシュに対するメソッド

h={"名前"=>"山崎", "年齢"=>60}
p h.key?("名前")
p h.key?("住所")

■ハッシュに対するメソッド

h={"名前"=>"山崎", "年齢"=>60}
h.each{|k,v| p k}
h.each{|k,v| p v}

■ハッシュに対するメソッド

h={"名前"=>"山崎", "年齢"=>60}
p h.map{|k,v| [k,v]}

■ハッシュで表をつくる

movies={}   # 最初に空のハッシュを作成する
movies[:君の名は]=  {高橋: 1,藤尾: 0, 寺井: 0, 羽太: 1}
movies[:シンゴジラ]={高橋: 1,藤尾: 1, 寺井: 0, 羽太: 0}
movies[:ジョーズ]=  {高橋: 1,藤尾: 0, 寺井: 0, 羽太: 1}
movies[:ピンポン]=  {高橋: 0,藤尾: 1, 寺井: 1, 羽太: 1}

p movies

■ハッシュの表を参照する

#加えて
p movies[:シンゴジラ]
p movies[:シンゴジラ][:羽太]

■ハッシュの表を参照する
#加えて
p movies[:君の名は]
p movies[:君の名は][:高橋]

■ハッシュの表の内容で計算する
#加えて
s=0
movies[:シンゴジラ].each{|k,v|s=s+v}
p s

■ハッシュの表の例２

t={}
t[:日本]={}
t[:ポーランド]={}
t[:セネガル]={}
t[:コロンビア]={}
t[:日本][:ポーランド]=[0,1]
t[:日本][:セネガル]=[2,2]
t[:日本][:コロンビア]=[2,1]
t[:ポーランド][:セネガル]=[1,2]
t[:ポーランド][:コロンビア]=[0,3]
t[:セネガル][:コロンビア]=[0,1]

■ハッシュの表の例２

# 上に加えて

p t[:日本][:ポーランド]

def kachiten(c )
    point=0
    t[c].each do |k,v|
                    if v[0] > v[1] then point=point+3
                    elsif v[0]==v[1] then point=point+1
                    end
                  end
    return point
end


■ハッシュを使った木構造

tree={a: {c: 1, d: 2}, b: {e: 3}}
p tree[:a][:d]   # 葉にアクセス

p tree[:b] 

■課題

次の表の完成形をハッシュで表現してください
各国の勝ち点を計算してください
勝ち点：勝利=3点、引き分け=1点、敗戦=0点
