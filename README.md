# website-logistik-kebon-ijo-yogyakarta
website kebon ijo dengan CI

![image](https://user-images.githubusercontent.com/40592735/221422964-6aa42ea7-fbf8-410e-a2ee-881359258330.png)

 
Pada tampilan website dengan menggukan code igniter 3 dsini akan menabhakan data barang ke dalam database untuk prosesnya akan tampil code seperti dibawah ini
 
public function proses_tambah(){
        if ($this->session->login['role'] == 'petugas'){
            $this->session->set_flashdata('error', 'Tambah data hanya untuk admin!');
            redirect('dashboard');
        }
 Untuk function proses tambah barang, disini ada syarat jika role tidak sama dengan admin maka tidak dapat melajutkan proses dan akan balik ke dashboard.
Dan jika sebagai admiin maka akan lanjut eksekusi code dibawah ini

![image](https://user-images.githubusercontent.com/40592735/221422987-c3511a07-a8db-474e-8e68-fb52c3e1d9bc.png)


$data = [
            'id_transaksi' => $this->input->post('kode_barang'),
            'id_supplier' => $this->input->post('nama_barang'),
            'nmasup' => $this->input->post('jumlah_input'),
            'kd_barang' => $this->input->post('harga_input'),
            'nmabar' => $this->input->post('satuan'),
            'jumlah' => $this->input->post('kondisi'),
            'harga' => $this->input->post('stok_awal'),
            'total' => $this->input->post('stok_terjual'),
            'waktu' => $this->input->post('stok_terjual'),
        ];
        
        
 Pada dasarnya ini adalah pengecekan dan penampungan semua inputan data ke dalam $data yang nnti jika benar maka akan lngsung eksekusi ke dalam model detail terima


if($this->m_detail_terima->tambah($data)){
            $this->session->set_flashdata('success', 'Data Barang <strong>Berhasil</strong> Ditambahkan!');
            redirect('barangmasuk');
        } else {
            $this->session->set_flashdata('error', 'Data Barang <strong>Gagal</strong> Ditambahkan!');
            redirect('barangmasuk');
        }
 
 
 Jika di model detail terima sudah banar data ersebut maka akan ditambahkan de dalam database dan data akan masuk kedalam database dengan pesan sukses

