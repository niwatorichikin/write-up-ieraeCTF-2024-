# write-up-ieraeCTF-2024-

68位でしたが自分は何も解けなかったのですが頑張った（先にチームメイトに通されてしまった）問題が一つあるのでそれについて書こうともいます




# derangement
ncしたりchallenge.pyを見て分かったのはinputで2を選んで15文字のmagic wordを入力するとflagが見れるらしい
1を選ぶとごちゃ混ぜになったmagic wordが出てくる、つまりそれぞれの列に一文字だけ出てこない文字がありそれを合体させたらmagic wordになる？ので何回か1を選んで出てこない文字を探すpythonを書こうとした,寮のネットが遅いし切れるし自分がpythonへたなのもありここまでに一時間もかかってしまった

    nc = Netcat("104.199.135.28",55555)

    nc.read()
    nc.write(b'1\n')

    pos = [] 
    for i in range(100):
        tmp = str(nc.read())

        key = list(str(tmp.split("type")[0][8:-2]))

        if i==0:
            pos = [key for _ in range(15)]
        print(key)

        for j in range(15):
            if key[j] in pos[j]:
                print("d")
                pos[j].remove(key[j])
        nc.write(b'1\n')
        print(i)
    nc.read()
    ans = ""
    print(pos)
    for p in pos:
        print(p)
        ans += p[0]
    nc.write(b'2')
    nc.write(ans.encode())
    print(nc.read())

ncうんぬんかんぬんの部分は先輩方のライブラリから拝借しました,
こんな感じだと思い実行するも思うようにいかずチームメイトに解かれてしまいました(ここまで二時間以上)



# まとめ
いままでプログラミングから逃げForensicsをやってきましたがそれだけじゃ何もできずチームにすら貢献できませんでした、そんなこともありとてもいい経験になりました！これからも前向きに学校にも負けず頑張っていきたいと思います！！！！！！！！
