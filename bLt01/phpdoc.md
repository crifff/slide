% Slide Show Headers

title: phpdocを書く
author: hoshina 

% Slides Start Here

#phpdocを書く

#PHPは静的解析に向いた動的言語
→入力時の補完が効かせやすい

　→入力効率の上昇・typoの抑制

　→コードを追いかけやすい

ランタイム時にしか決定できないような箇所でもドキュメントで補える

#ドキュメント|コメントに何を書くか
* コードだけではわからないこと
  * 目的・背景
  * 他の要素との相互作用
* 説明してくれたほうが手っ取り早いもの
  * 使用方法
  * 拡張方法
* IDEの補完機能へのヒント

etc

#phpdocで書ける要素
[http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html](http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html)

@abstract
@access
@author
@category
@copyright
@deprecated
@example
@final
@filesource
@global
@ignore
@internal
@license
@link
@method
@name
@package
@param
@property
@return
@see
@since
@static
@staticvar
@subpackage
@todo
@tutorial
@uses
@var
@version

#関数・メソッドの引数と返り値を指定する

<% coderay :lang=>'php' do %>
<?php
/**
 * 関数の説明
 * @param int $int 引数1の説明
 * @param string $string 引数2の説明
 * @param array $array 引数3の説明
 * @param Object $object 引数4の説明
 * @param Object[] $objList 引数5の説明
 * @return Object[] 返り値の説明
 */
function hoge($int, $string, $array, $object, $objList){
	$id = $object->id; //補完できる
	$id = $object[1]->id; //補完できる
	return $objList;
}
<% end %>

#型の表記に注意

* phpの型で書く
  * typeとかvarcharという型は存在しないよ
* ネームスペースを考慮する
  * そのファイルのnamespaceに依存する
  * Eclipceはフルパスじゃないと認識してくれない…
    * NetBeansかPhpStormにしよう

#プロパティの中身を明示する

<% coderay :lang=>'php' do %>
<?php
class Hoge {
	/** @var Object $object 変数の説明 **/
	private $object;

	public function setup(){
		$this->object = new Object();
	}

	public function getObjectId(){
		return $this->object->id; // 補完できる
	}
}
<% end %>

#変数の中身を明示する

<% coderay :lang=>'php' do %>
<?php

function hoge($list){
	/** @var Object[] $list オブジェクトの配列 **/
	$list = array_filter($list, function(Object $item){
			return $item !== NULL;
		});
	return $list[0]->id; //補完できる
}
<% end %>

#[応用]実態のないプロパティ|メソッドの補完

<% coderay :lang=>'php' do %>
<?php

/**
 * @property Object[] $objects プロパティの説明
 * @method Object getObject(int $id) メソッドの説明 
 */
class Hoge{

}

$tmp = new Hoge();
$tmp->objects[1]->id; //補完できる
$tmp->getObject(1); //補完できる
<% end %>

#[応用]関連するメソッド等を明示する

<% coderay :lang=>'php' do %>
<?php

class Hoge{
	/**
	 * メソッドの説明
	 * @see Fuga::f()
	 */
	static public function f(){
		$fuga = new Fuga;
		return $fuga->f();
	}
}

class Fuga{
	static public function f(){
		return 1;
	}
}
<% end %>


#おしまい
