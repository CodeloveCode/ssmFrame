文件路径表FILE_PATHS：
id_filepaths本表主键,事项类型item（如：工业产品，机动车），办件主键item_pk,文件路径path，文件名fileName，文件类型type（0是单个附件，1是批量下载的附件包），文件个数fileNum（给批量下载用，防止前一次附件没有下载全）
思路：
一。定时扫描145库的附件表，将附件下载到文件系统
a.查询附件表，将没下载过的附件，存入文件系统。
c.将文件路径信息存入路径表。
b.更新附件表的标志位，下次不查询。
二。用户点击单个文件的链接时，提供下载
a.根据附件主键，去路径表查询路径信息
b。根据路径读取文件
c。提供下载


1.自动下载监听器,部署前要把注解放开.保证可以进行扫描
2.修改AttachmentMapper.xml中的一次下载数据量
3.修改log4j.

项目下载页位置:
工业产品:web2\jsp\business\businfo.jsp
工业产品集团公司:web2\jsp\business\businfoJT.jsp
机动车:web2/jsp/business/jdchaqjcjghzhNew.jsp
